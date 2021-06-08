# SOLID 원칙  

## 5. DIP(Dependency Inversion Principle): 의존성역전의 원칙  

> 상위 수준 정책은 하위 수준 세부 정보에 의존해서는 안 된다.  
> 상위 모듈은 하위 모듈의 구현에 의존해서는 안 된다.  
> 하위의 모듈이 상위 모듈에 정의한 추상 타입에 의존 해야 한다.
> * 핵심: 의존 관계를 맺을 때 변화하기 쉬운 것에 의존하기보다 변화하지 않는 것에 의존하라는 원칙. 

## 효과  
* IOC, Hook Method, 확장성이라는 핵심 요소가 조합되어 복잡한 컴포넌트들의 관계를 단순화하고 컴포넌트 간의 커뮤니케이션을 효율적이게 한다.  
* 복잡하고 지난한 컴포넌트 간의 커뮤니케이션 관계를 단순화하기 위한 원칙   


## 적용방법  
1. 비동기적으로 커뮤니케이션이 이뤄져야 하거나 이뤄져도 될 경우, 컴포넌트 간의 커뮤니케이션이 복잡할 경우, 컴포넌트 간의 커뮤니케이션이 비효율적일 경우(빈번하게 확인이 필요한 구조)에 사용된다. 

2. 레이어링  
Transitive Dependency가 발생했을 때 상위 레벨의 레이어가 하위 레벨의 레이어를 바로 의존하게 하는 것이 아니라 이 둘 사이에 존재하는 추상레벨을 통해 의존해야 한다.  
상위레벨의 모듈은 하위레벨의 모듈로의 의존성에서 벗어나 그 자체로 재사용되고 확장성도 보장 받을 수 있다.  
이를 도식화 하면 아래와 같다.  
<img src="https://github.com/copazima/interview/blob/main/resource/layer.png?raw=true" width="450" height="250">

## 적용사례  
* DIP 준수하지 않은 코드  

![blog](https://i.imgur.com/Zkykv9m.png)  
카드 결제(상위 수준 정책)가 신한 카드 결제(하위 수준)에 의존하고 있다.  

* 지나친 의존관계
```
class PaymentController {
    @RequestMapping(value = "/dip/anti/payment", method = RequestMethod.POST)
    public void pay(@RequestBody ShinhanCardDto.PaymentRequest req){
        shinhanCardPaymentService.pay(req);
    }   
}
class ShinhanCardPaymentService {
    public void pay(ShinhanCardDto.PaymentRequest req) {
        shinhanCardApi.pay(req);
    }   
}

// RequestBody JSON 포멧
{
  "shinhanCardNumber":"0000-1111-2222-3333",  //만약 shinhanCardNumber -> cardNumber 으로 변경된다면 ?
  "cvc":"233"
}
```
카드 결제 기능(상위 정책)이 신한 카드 결제(하위 정책)에 지나치게 의존적이다. 그 결과 위처럼 신한 카드사의 카드 결제의 JSON의 키값만 변경 시 컨트롤러, 그 값을 넘겨주는 프론트엔드 변경까지 영향을 미치게 된다.  
지나친 의존 관계는 많은 변경 포인트를 유발한다.  


* 확장에 유연하지 못함  
```
@RequestMapping(value = "/anti/payment", method = RequestMethod.POST)
public void pay(@RequestBody CardPaymentDto.PaymentRequest req){
    if(req.getType() == CardType.SHINHAN){
        shinhanCardPaymentService.pay(req);
    }else if(req.getType() == CardType.WOORI){
        wooriCardPaymentService.pay(req);
    }
}
```
우리카드, 신한 카드 결제 요청을 받을 PaymentRequest Dto 클래스를 생성했고 CardType으로 해당 되는 카드 타입에 맞는 서비스를 호출하는 구조이다. 카드가 지속해서 추가될 때마다 해당 카드결제를 위한 if문을 지속해서 추가해야 한다. 
이 외에도 추가될 카드의 결제를 담당하는 XXXPaymentService 클래스들의 의존성이 이루어진다. 그 결과 PaymentController에는 컨트롤러 계층임에도 너무 많은 책임을 갖게 되며, 확장이 어렵고 변경에 취약한 구조가 된다. 

---

* DIP 준수 한 코드 
![DIP](https://i.imgur.com/TdGYl8n.png)  

- 상위 모듈(카드 결제)은 하위 모듈(신한 카드 결제)의 구현에 의존해서는 안 된다. 하위의 모듈(신한 카드 결제)이 상위 모듈(카드 결제)에 정의한 추상 타입(인터페이스)에 의존해야 한다. 

```
class PaymentController {
    @RequestMapping(value = "/payment", method = RequestMethod.POST)
    public void pay(@RequestBody CardPaymentDto.PaymentRequest req) {
        final CardPaymentService cardPaymentService = cardPaymentFactory.getType(req.getType());
        cardPaymentService.pay(req);
    }
}

public interface CardPaymentService {
    void pay(CardPaymentDto.PaymentRequest req);
}

public class ShinhanCardPaymentService implements CardPaymentService {
    @Override
    public void pay(CardPaymentDto.PaymentRequest req) {
        shinhanCardApi.pay(req);
    }
}
```
의존관계를 인터페이스를 통해 의존성을 역전 시켰다. 컴파일 단계에서는 PaymentController는 PaymentService 인터페이스를 바라보지만 런타임에서는 cardPaymentFactory를 통해 ShinhanCardPaymentService를 바라보게 된다.  
또 하위 정책의 신한 카드, 우리 카드가 변경되더라도 PaymentService 인터페이스를 의존하고 있으므로 확장에 열려 있고 변경에는 닫혀 있는 OCP를 준수하게 된다. 


> 참고자료  
[https://velog.io/@hanblueblue/Java-SOLID-SRP-OCP-LSP-ISP-DIP]  
[https://cheese10yun.github.io/spring-solid-dip/]  

작성자: 다정  
작성일: 21.6.7
