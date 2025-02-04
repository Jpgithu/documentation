---
aliases:
- /ko/account_management/faq/how-do-i-reset-my-application-keys/
- /ko/agent/faq/how-do-i-reset-my-datadog-api-keys/
- /ko/account_management/faq/api-app-key-management/
kind: faq
title: API와 애플리케이션 키
---

## API 키

API 키는 조직에 고유하게 할당됩니다. Datadog Agent에서 메트릭과 이벤트를 Datadog로 전송하려면 [API 키][1]가 필요합니다.

## 애플리케이션 키

조직의 API 키와 조합하여 [애플리케이션 키][2]를 사용하면 Datadog 프로그램 API에 액세스할 수 있습니다. 애플리케이션 키는 키를 생성한 사용자 계정과 연계되며, 기본적으로 생성한 사용자의 접근 허용 권한과 범위를 갖추고 있습니다.

### 범위

<div class="alert alert-info"> 애플리케이션 키의 인증 범위는 비공개 베타 기능입니다. 조직에서 범위가 제한(scoped)된 애플리케이션 키를 지원받고자 하는 경우  <a href="https://www.datadoghq.com/support/">Datadog 고객 지원팀</a>에 문의하시기 바랍니다. </div>

애플리케이션을 더욱 안전하게 보호하기 위해 애플리케이션 키의 [인증 범위][3]를 지정하여 권한 허용 여부를 한층 세밀하게 정의하고, 애플리케이션이 갖는 Datadog 데이터 액세스 권한을 최소화할 수 있습니다. 이를 통해 애플리케이션 액세스 권한을 정밀하게 관리하고, 과잉 액세스를 제한하여 보안 취약점 최소화가 가능합니다. 예를 들어 대시보드 읽기 기능만 필요한 애플리케이션은 사용자를 관리하는 관리자 권한이나 조직 데이터 삭제 권한을 가질 필요가 없습니다.

모범 사례로 권장하는 애플리케이션 키 범위 설정은 키에 최소한의 우선권을 부여하고, 애플리케이션이 의도에 맞추어 기능하는 데 필요한 권한만을 허용하는 것입니다. 범위가 제한된 애플리케이션 키는 사용자가 지정한 범위만을 활용하며 그 이외의 추가 권한이 없습니다. 애플리케이션 키의 인증 범위는 언제든지 변경 가능합니다. 단, 범위 변경 시 애플리케이션의 기존 기능이나 액세스에 어떤 영향을 미칠지 고려해야 합니다.

**참조**:

- 애플리케이션 키 생성/수정 [권한이 허용된][4] 사용자나 서비스 계정은 애플리케이션 키의 범위를 지정할 수 있습니다. 사용자가 보유한 애플리케이션 키의 범위를 지정하려면 `user_app_keys` 권한이 필요합니다. 소속 조직의 다른 사용자가 보유한 애플리케이션 키의 범위를 지정하려면 `org_app_keys_write` 권한이 필수입니다. 사용자가 서비스 계정 애플리케이션 키의 범위를 지정하려면 `service_account_write` 권한이 있어야 합니다.
- 애플리케이션 소유자가 필수 권한을 상실하는 경우 애플리케이션을 인증할 수 없습니다. 보유하지 않은 인증 범위로 애플리케이션 키의 범위를 지정한 경우에도 마찬가지입니다.
- 애플리케이션 키를 생성하거나 애플리케이션을 인증할 때 권한 상실로 인한 오류가 발생하면 `403 Forbidden` 오류가 표시됩니다. 다양한 오류 반응에 대한 자세한 정보는 [Datadog API][5] 설명서를 참조하세요.
- 사용자의 역할이나 권한이 변경된 경우에도, 애플리케이션 키에 설정한 인증 범위는 변경 없이 유지됩니다.

## 클라이언트 토큰

보안상의 이유로 브라우저에서 API 키를 사용하여 데이터를 전송할 수 없습니다. 자바스크립트(Javascript) 코드를 통해 API 키가 클라이언트 측에 노출되기 때문입니다. 대신 웹 브라우저와 기타 클라이언트에서 Datadog로 데이터를 전송하려면 클라이언트 토큰을 사용해야 합니다.

클라이언트 토큰을 사용해야 데이터 전송이 가능한 클라이언트는 여러 유형이 있습니다. 예시는 다음과 같습니다.
- [웹 브라우저 로그 컬렉터(Collector)][6]는 로그를 제출합니다.
- [Real User Monitoring][7] 애플리케이션은 이벤트와 로그를 제출합니다.

클라이언트는 조직마다 고유합니다. 클라이언트 토큰을 관리하려면 **Organization Settings**에서 **Client Tokens** 탭을 클릭하세요.

**참조:** 클라이언트 토큰을 생성한 사용자가 비활성화된 경우에도 클라이언트 토큰은 활성화 상태로 유지됩니다.

## API 키 또는 클라이언트 토큰 추가

Datadog API 키나 클라이언트 토큰을 추가하려면:

1. Organization settings로 이동한 다음, **API keys** 또는 **Client Tokens** 탭을 클릭합니다.
2. 키를 생성하는지, 토큰을 생성하는지 여부에 따라 **New Key** 또는 **New Client Token** 버튼을 클릭합니다.
3. 키나 토큰의 이름을 입력합니다.
4. **Create API key** 또는 **Create Client Token**을 클릭합니다.

**참조**:

- 소속된 조직이 최소 한 개 이상, 최대 50개 이하의 API 키를 보유해야 합니다.
- 키 이름은 조직에서 중복 사용되지 않는 고유 명칭이어야 합니다.

## API 키 또는 클라이언트 토큰 삭제

Datadog API 키나 클라이언트 토큰을 삭제하려면 키나 토큰 목록으로 이동한 다음, 삭제할 키나 토큰 옆에 있는 **쓰레기통** 아이콘을 클릭하세요. 쓰레기통에는 **Revoke**라고 쓰여 있습니다.

## 애플리케이션 키 추가

Datadog 애플리케이션 키를 추가하려면 **Organization Settings** > **Application Keys**로 이동하세요. 애플리케이션 키 생성 [권한이 있는 경우][4] **New Key**를 클릭합니다.

**참조**:

- 애플리케이션 키 이름은 필수 입력 항목입니다.

## 애플리케이션 키 삭제

Datadog 애플리케이션 키를 삭제하려면 **Organization Settings** > **Application Keys**로 이동하세요. 애플리케이션 키 생성 및 관리 [권한이 있는][4] 경우, 보유한 키를 볼 수 있습니다. 삭제하고자 하는 키 옆의 **Revoke**를 클릭하세요. 조직의 모든 애플리케이션 키를 관리할 권한을 보유했다면, 삭제하고자 하는 키를 검색한 다음 옆에 표시된 **Revoke**를 클릭하면 됩니다.

## 애플리케이션 키 범위 설정

애플리케이션 키의 [인증 범위][3]를 지정하려면 [Datadog API][5]로 애플리케이션 생성 또는 수정 리퀘스트를 전송하세요. 범위는 [현재 사용자][8] 또는 [서비스 계정][9]에서 보유한 애플리케이션 키를 대상으로 지정 가능합니다. 본 항목이 지정되지 않은 경우, 애플리케이션 키는 기본으로 생성한 사용자와 동일한 범위와 권한을 갖습니다.

**참조**:

- 범위 이름은 대소문자를 구별합니다.

## 여러 API 키 사용

조직에서 여러 API 키를 사용하는 환경을 고려해보세요. 예를 들어 각 배포 방식마다 다른 API 키를 사용하는 경우가 있습니다. AWS의 쿠버네티스(Kubernetes)에 Agent를 배포하는 용도의 키, Chef를 사용하여 온프레미스로 배포하는 용도의 키, 대시보드나 모니터링을 자동화하는 Terraform 스크립트용 키, 로컬에서 배포하는 개발자용 키 등등을 전부 다르게 사용하는 것입니다.

여러 API 키를 사용하면 보안 대책의 일부로서 키를 회전시킬 수 있고, 특정 키가 부주의로 노출되었거나 해당 키와 연계된 서비스 이용을 중단하고자 하는 경우에 키 권한을 취소할 수 있습니다.

API 키를 최대 50개로 제한하는 기본 한도를 넘어서, 조직에 그 이상의 키가 필요한 경우 [지원팀][10]에 문의해 한도 상향을 요청해주세요.

## 사용자 계정 비활성화

사용자 계정이 비활성화되면 해당 사용자가 생성한 애플리케이션 키의 권한이 취소됩니다. 비활성화된 계정에서 생성한 모든 API 키가 삭제되지는 않으며, 여전히 유효합니다.

## 키의 전송

보안을 위하여, Datadog는 API/애플리케이션 키를 사용자 간에 전송하지 않습니다. 모범 사례로 권장하는 방법은 API/애플리케이션 키를 지속 추적하다가, 사용자가 회사를 그만둔 후에 해당 키를 회전시키는 것입니다. 이렇게 하면 퇴직한 사용자는 더 이상 계정과 Datadog API에 접근할 수 없습니다. API/애플리케이션 키를 전송한 경우 퇴직한 사용자가 계속해서 Datadog API에서 데이터를 송수신할 수 있습니다. API/애플리케이션 키가 연계된 핸들을 변경해달라고 요청하는 고객 여러분도 계시지만, 이는 근본적인 문제 해결책이 아닙니다. 회사를 그만둔 사용자가 계속해서 Datadog API에서 데이터를 송수신할 수 있다는 문제를 해결하지 못하기 때문입니다.

또 API/애플리케이션 키를 보유하기 위해 "서비스 계정"을 만들 수 있는지 수 차례 문의를 받기도 하였습니다. "서비스 계정"을 사용하여 API 키를 보유하는 것이 합리적인 경우도 다수 존재합니다. 단, 서비스 계정이란 누구나 접속 가능한 공유 계정 이상의 기능을 한다는 사실을 주지하셔야 합니다. "서비스 계정" 사용을 계획하는 경우, 최소 권한의 원칙을 적용하고 서비스 계정의 자격증명을 (패스워드 매니저 사용 등의 방법으로)안전하게 보관하는 것이 중요합니다. 서비스 계정 자격증명이 유출되는 사고가 발생하지 않도록 막으려면, 액세스는 소규모로 제한해야 합니다. 액세스 범위는 계정을 유지 관리하는 사용자로만 한정하는 것이 가장 바람직합니다.

## API나 애플리케이션 키가 노출된 경우의 대책

비공개 키(프라이빗 키)가 해킹당하거나 공개적으로 노출된 경우, 계정 보안을 위해 최대한 신속하게 조치를 취해야 합니다. GitHub를 비롯한 공개 사이트에서 키가 포함된 파일을 삭제하는 것만으로는 보안이 보장되지 **않습니다**. 이미 타인이 파일에 접근했을 가능성이 있기 때문입니다.

다음의 절차를 따라 계정을 보호하세요.

**참조**: 활성화 상태인 키의 권한을 취소(revoke)하면 서비스에 영향을 미칠 수 있습니다. 사용 범위가 크거나 미정인 경우, 영향을 받은 키의 권한을 취소하기 **전에** 2-5단계를 고려해보세요.

1. 영향을 받은 키의 권한을 취소합니다.
2. 공개적으로 액세스 가능한 파일에서 비공개 키를 포함한 코드를 삭제합니다.
    - 공개 리포지토리에 보안 처리된(sanitized) 파일을 게시합니다.
    - 커밋 히스토리(commit history)에서 민감한 데이터를 삭제합니다.
3. 신규 키를 생성합니다.
4. 영향을 받은 서비스를 새로운 키로 업데이트합니다.
5. 계정의 무단 액세스가 있는지 검토합니다.
    - 최근에 추가된 사용자
    - 새로운 리소스
    - 역할 또는 권한 변경

비정상적인 활동이 탐지되었거나 계정 보안을 위해 추가로 도움이 필요한 경우,  [Datadog 고객 지원팀][10]에 문의하세요.

## 트러블슈팅

도움이 필요하신가요? [Datadog 고객 지원팀][10]에 문의해주세요.

[1]: https://app.datadoghq.com/organization-settings/api-keys
[2]: https://app.datadoghq.com/access/application-keys
[3]: /ko/api/latest/scopes/
[4]: /ko/account_management/rbac/permissions
[5]: /ko/api/latest/key-management/
[6]: /ko/logs/log_collection/javascript/
[7]: /ko/real_user_monitoring/
[8]: /ko/api/latest/key-management/#create-an-application-key-for-current-user
[9]: /ko/api/latest/service-accounts/
[10]: /ko/help/