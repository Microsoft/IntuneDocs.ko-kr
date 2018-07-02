## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 사용

자동 등록을 사용하면 작업 계정을 자신의 개인 소유의 장치에 추가하거나 Azure Active Directory로 회사 소유의 장치를 연결할 때 Intune에서 Windows 10 장치를 등록할 수 있습니다. 사용자 장치는 백그라운드에서 등록되어 Azure Active Directory에 가입됩니다. 등록이 되고 나면 Intune으로 장치를 관리할 수 있습니다.

**필수 구성 요소**
- Azure Active Directory Premium 구독([평가판 구독](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 구독


### <a name="configure-automatic-mdm-enrollment"></a>자동 MDM 등록 구성

1. [Azure 관리 포털](https://portal.azure.com)(https://manage.windowsazure.com) 에 로그인하여 **Azure Active Directory**를 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-azure-main.png)

2. **이동성(MDM 및 MAM)** 을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-mdm.png)

3. **Microsoft Intune**을 선택합니다.

   ![Azure Portal의 스크린샷](../media/auto-enroll-intune.png)

4. **MDM 사용자 범위**를 구성합니다. Microsoft Intune에서 관리해야 하는 사용자의 장치를 지정합니다. 이러한 사용자의 Windows 10 장치는 Microsoft Intune을 사용한 관리에 자동으로 등록됩니다.

   - **없음**
   - **일부**
   - **모두**

   ![Azure Portal의 스크린샷](../media/auto-enroll-scope.png)

5. 다음 URL의 기본값을 사용합니다.
   - **MDM 사용 약관 URL**
   - **MDM 검색 URL**
   - **MDM 규정 준수 URL**

6. **저장**을 선택합니다.

기본적으로 2단계 인증이 서비스에 대해 활성화되어 있지 않습니다. 그러나 장치를 등록할 때 2단계 인증이 권장됩니다. 이 서비스에 대해 2단계 인증을 요구하기 전에 Azure Active Directory에서 2단계 인증 공급자를 구성하고 다단계 인증에 대한 사용자 계정을 구성해야 합니다. [Azure Multi-Factor Authentication Server 시작](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.
