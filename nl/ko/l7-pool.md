---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 계층 7 풀
{: #layer-7-pool}

계층 7(L7) 풀은 수신 요청을 처리하기 위한 서버(멤버)의 논리 그룹입니다.

계층 7 로드 밸런싱 기능은 정책 및 규칙을 기반으로 수신 트래픽을 여러 백엔드 풀로 전달할 수 있습니다. 이 기능은 다중 7 풀을 로드 밸런서와 연관시켜서 지원됩니다. 계층 7 풀은 조치가 `redirect to pool`인 계층 7 정책과 함께 사용됩니다.

L7 풀은 HTTP만 백엔드 프로토콜로 지원합니다.

## 세션 지속성
각 계층 8 풀에 대한 세션 지속성을 구성할 수 있습니다. 세부사항은  
[고급 트래픽 섹션](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-advanced-traffic-management-with-ibm-cloud-load-balancer)을 참조하십시오.

## 계층 7 멤버

계층 7 풀과 연관된 백엔드 서버를 계층 7 멤버라고 합니다.

매번 다른 포트 번호를 지정하여 동일한 백엔드 서버를 L7 풀에 여러 번 추가할 수 있습니다.

## 상태 검사 구성
각 계층 7 풀에 대한 상태 검사 정의는 필수입니다. 시스템에서 L7 풀에 대한 기본 상태 검사 구성을 미리 채웁니다.

애플리케이션 요구사항에 맞게 이러한 설정을 사용자 정의할 수 있습니다.

 * **간격**: 두 번의 연속 상태 검사 시도 사이의 간격(초)입니다.
 * **제한시간**: 시스템에서 상태 검사 요청에 대한 응답을 기다리는 최대 시간입니다.
 * **최대 시도 수**: 서비스를 비정상으로 선언하기 전에 시스템에서 시도하는 최대 추가 상태 검사 횟수입니다.
 * **URL 경로**: 계층 7 상태 검사를 위한 HTTP URL 경로입니다.
