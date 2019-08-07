---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-07"

keywords: about, load balancer, overview, features

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# {{site.data.keyword.loadbalancer_full}} 정보
{: #about-ibm-cloud-load-balancer}

{{site.data.keyword.loadbalancer_full}} Service는 다중 애플리케이션 서버 인스턴스에 트래픽을 분배하고 트래픽을 양호한 상태의 인스턴스에만 전달하여 고객이 비즈니스 중심 애플리케이션의 가용성을 향상시키는 데 도움을 줍니다.

## 기능 개요
{: #overview-of-features}

{{site.data.keyword.loadbalancer_full}} Service는 다음 기능을 제공합니다.

* 공용(인터넷 연결) 로드 밸런서
	* 완전한 도메인 이름(FQDN)을 통해 공용으로 액세스 가능한 서비스
	* 개인용 서브넷의 백엔드 서버 인스턴스
* 내부 로드 밸런서
	* 완전한 도메인 이름(FQDN)을 통해 개인용으로 액세스 가능한 서비스
	* 클라이언트 요청이 사설 네트워크 상에서 라우팅됨
	* 개인용 서브넷의 백엔드 서버 인스턴스
* 기본 로드 밸런싱
	* 계층-4 애플리케이션 포트 정보 기반의 트래픽 분배
	* HTTP, HTTPS 및 TCP 기반 애플리케이션에 대한 지원
	* 다양한 로드 밸런싱 방법(예: 라운드 로빈(RR), 가중치 라운드 로빈 및 최소 연결)
	* 데이터 센터 내에 로컬로 상주하는 Bare Metal 컴퓨팅 인스턴스 및 Virtual Server 간의 로드 밸런싱
* 서버 상태 검사
	* 트래픽을 양호한 상태의 서버에만 전달하는지를 확인하는 서버 상태에 대한 주기적인 모니터링
	* TCP 포트의 계층 4-상태 검사 및 HTTP 포트의 계층-7 상태 검사
* SSL 오프로드
	* 백엔드 서버와의 일반 텍스트 HTTP 통신을 사용한 수신 SSL(HTTPS) 트래픽의 종료
* 고급 트래픽 관리
	* 클라이언트 연결 유지(세션 지속성)
	* 가상 포트당 최대 연결
* 직관적인 그래픽 인터페이스 및 API를 사용한 쉬운 관리
* 기본 제공 신뢰성
* 종량제
* 모니터링
    * 사용자가 지정한 시간 간격에 HTTP, HTTPS 및 TCP 프로토콜에 대한 처리량, 활성 연결 수 및 연결 속도 메트릭을 모니터합니다. 추가 세부사항은 [모니터링 메트릭](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-monitoring-metrics-with-ibm-cloud-load-balancer)을 참조하십시오.
* 계층 7 지원
    * HTTP/HTTPS 트래픽은 HTTP 헤더를 기반으로 여러 백엔드 서비스로 라우팅되고 정책 및 규칙을 사용하여 수행됩니다. 규칙은 트래픽을 분류하는 데 사용되고 HTTP 헤더 필드를 기반으로 합니다. 트래픽이 모든 규칙과 일치하면 정책에 지정된 조치가 수행됩니다.
* MZR(Multi-Zone Region) 지원
    * 로드 밸런서 노드는 MZR의 여러 다른 센터에서 인스턴스화됩니다. 자세한 정보는 [MZR(Multi-Zone Region) 개요](/docs/infrastructure/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)를 참조하십시오.
* 데이터 로그
    * 데이터 로그가 사용으로 설정되면 로드 밸런서 로그가 [IBM Cloud 로그 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}에 전달됩니다. 고객은 [IBM Cloud 로그 분석 서비스![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/log-analysis){:new_window}를 사용하여 데이터 로그를 볼 수 있습니다. 
