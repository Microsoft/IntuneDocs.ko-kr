## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 사용

자동 등록을 통해 사용자가 Intune에 Windows 10 디바이스를 등록할 수 있습니다. 등록하려면 사용자가 회사 계정을 개인적으로 소유한 디바이스에 추가하거나 회사 소유 디바이스를 Azure Active Directory에 연결합니다. 디바이스는 백그라운드에서 등록되어 Azure Active Directory에 연결됩니다. 등록된 디바이스는 Intune을 통해 관리됩니다.

**필수 구성 요소**
- Azure Active Directory Premium 구독([평가판 구독](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 구독


### <a name="configure-automatic-mdm-enrollment"></a>자동 MDM 등록 구성

1. [Azure Portal](https://portal.azure.com)에 로그인하고 **Azure Active Directory**를 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-azure-main.png)

2. **이동성(MDM 및 MAM)** 을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-mdm.png)

3. **Microsoft Intune**을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-intune.png)

4. **MDM 사용자 범위**를 구성합니다. Microsoft Intune에서 관리해야 하는 사용자의 디바이스를 지정합니다. 이러한 Windows 10 디바이스는 Microsoft Intune을 사용한 관리에 자동으로 등록됩니다.

   - **없음** - MDM 자동 등록 사용 안 함
   - **일부** - Windows 10 장치를 자동으로 등록할 수 있는 **그룹** 선택
   - **모두** -모든 사용자가 Windows 10 장치를 자동으로 등록할 수 있음

      > [!IMPORTANT]
      > 그룹에 대해 **MAM 사용자 범위** 및 자동 MDM 등록(**MDM 사용자 범위**)을 모두 사용할 수 있는 경우 MAM만 사용하도록 설정됩니다. 작업 공간을 개인 디바이스에 연결하는 경우 해당 그룹의 사용자에 대해 MAM만 추가됩니다. 디바이스는 자동으로 MDM을 등록하지 않습니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-scope.png)

5. 다음 URL의 기본값을 사용합니다.
    - **MDM 사용 약관 URL**
    - **MDM 검색 URL**
    - **MDM 규정 준수 URL**

6. **저장**을 선택합니다.

기본적으로 2단계 인증이 서비스에 대해 활성화되어 있지 않습니다. 그러나 디바이스를 등록할 때 2단계 인증이 권장됩니다. 2단계 인증을 요구하려면 Azure AD에서 2단계 인증 공급자를 구성하고 다단계 인증에 대한 사용자 계정을 구성합니다. [Azure Multi-Factor Authentication Server 시작](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.
