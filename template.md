---
title:
- 문서 제목 | 서비스 이름
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: d05559a46cfd2bf9e092378e7cff779022e21792
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509645"
---
# <a name="metadata-and-markdown-template"></a>메타데이터 및 Markdown 템플릿

이 docs.ms 템플릿에는 markdown 구문 예제와 메타데이터 설정 지침이 포함되어 있습니다. 이 템플릿은 각 EM 파일럿 리포지토리의 루트 디렉터리(예: ~/Azure-RMSDocs-pr /template.md)에서 사용할 수 있으며 [게시된 버전](https://stage.docs.microsoft.com/en-us/rights-management/template)을 참조하여 markdown 예제가 어떻게 렌더링되는지 확인할 수 있지만 markdown 파일로 읽도록 작성되었습니다.

markdown 파일을 만드는 경우 템플릿을 새 파일에 복사하고 아래 지정된 대로 메타데이터를 입력한 다음 문서 제목 위의 H1 제목을 설정하고 콘텐츠를 삭제합니다. 


## <a name="metadata"></a>메타데이터 

전체 메타데이터 블록이 필수 필드와 선택적 필드로 구분되어 위에 나와 있습니다. 자세한 내용은 [OPS 메타데이터 치트시트(cheatsheet)](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)를 참조하세요. 몇 가지 주요 참고 사항:

- 콜론(:)과 메타데이터 요소 값 사이에 **반드시** 공백이 있어야 합니다.
- 선택적 메타데이터 요소에 값이 없는 경우 #을 사용하여 요소를 주석으로 처리합니다. 비워 두거나 "na"를 사용하지 마세요. 주석으로 처리된 요소에 값을 추가하는 경우 #을 제거해야 합니다.
- 값(예: 제목)에 콜론이 있으면 메타데이터 파서가 중단됩니다. 해당 위치에 HTML 인코딩 &#58;을 사용합니다(예: "제목: Azure 권한 관리&#58; 기본 사항 | Azure RMS").
- **title**: 이 제목은 검색 엔진 결과에 표시됩니다. 제목은 파이프(|)와 서비스 이름으로 끝나야 합니다(예: 위 참조). 제목은 H1 제목의 제목과 일치하지 않아도 됩니다(또는 일치하지 않아야 함). 대략 65자 정도여야 합니다(| 서비스 이름 포함).
- **author**, **manager**, **reviewer**: author 필드에는 만든 이의 별칭이 아니라 **Github 사용자 이름**이 포함되어야 합니다.  반면, "manager" 및 "reviewer" 필드에는 별칭이 포함되어야 합니다. ms.reviewer는 문서 또는 서비스와 관련된 PM의 이름을 지정합니다.
- **ms.assetid**: CAPS에 있는 문서의 GUID입니다. 새 markdown 파일을 만들 때 [https://www.guidgenerator.com](https://www.guidgenerator.com)에서 GUID를 가져옵니다. 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: 이러한 요소의 가능한 값은 [여기](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)서 확인할 수 있습니다.

## <a name="basic-markdown-and-gfm"></a>기본 Markdown 및 GFM

모든 기본 markdown과 Github 버전이 지정된 markdown이 지원됩니다. 자세한 내용은 다음을 참조하세요.

- [기본 markdown 구문](https://daringfireball.net/projects/markdown/syntax)
- [GFM(Github 버전이 지정된 markdown) 설명서](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>제목

첫 번째 및 두 번째 수준 제목의 예는 위에 나와 있습니다. 

항목에 첫 번째 수준 제목은 **반드시** 하나만 있어야 하며, 페이지 제목으로 표시됩니다.  

두 번째 수준 제목은 페이지 제목 아래에 있는 "이 문서의 내용" 섹션에 표시되는 페이지 목차를 생성합니다.

### <a name="third-level-heading"></a>세 번째 수준 제목
#### <a name="fourth-level-heading"></a>네 번째 수준 제목
##### <a name="fifth-level-heading"></a>다섯 번째 수준 제목
###### <a name="sixth-level-heading"></a>여섯 번째 수준 제목

## <a name="text-styling"></a>텍스트 스타일

*기울임꼴* 

**굵게** 

~~취소선~~



## <a name="links"></a>링크

동일한 리포지토리에 있는 markdown 파일에 연결하려면 [상대 링크](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)를 사용합니다. 

- 예: [Azure 권한 관리란?](./understand-explore/what-is-azure-rights-management.md)

동일한 markdown 파일에 있는 헤더에 연결하려면 게시된 문서의 원본을 보고 헤드 ID(예: `id="blockquote"`)를 찾은 다음 # + ID(예: `#blockquote`)를 사용하여 연결합니다.

- 예: [Blockquotes](#blockquote)

동일한 리포지토리에 있는 markdown 파일의 헤더에 연결하려면 상대 링크 + 해시태그 링크를 사용합니다.

- 예: [등록 프로세스의 기술 개요](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

외부 파일에 연결하려면 전체 URL을 링크로 사용합니다.

- 예: [Github](http://www.github.com)

URL이 markdown 파일에 표시되는 경우 클릭할 수 있는 링크로 변환됩니다.

- 예: http://www.github.com

## <a name="lists"></a>목록

### <a name="ordered-lists"></a>순서가 지정된 목록

1. 키에 
1. Is
1. An
1. Ordered
1. 목록  


#### <a name="ordered-list-with-an-embedded-list"></a>포함된 목록이 있는 순서가 지정된 목록

1. 서명
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. 목록


### <a name="unordered-lists"></a>순서가 지정되지 않은 목록

- 키에
- is
- a
- bulleted
- 목록


##### <a name="unordered-list-with-an-embedded-lists"></a>포함된 목록이 있는 순서가 지정되지 않은 목록

- 이 
- bulleted 
- 목록
    - Mrs. Peacock
    - Mr. Green
- 포함  
- 기타
    1. Colonel Mustard
    1. Mrs. White
- lists


## <a name="horizontal-rule"></a>가로줄

---

## <a name="tables"></a>테이블

| 테이블        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| col 1 is default | left-aligned     |    $1 |


## <a name="code"></a>코드

### <a name="codeblock"></a>Codeblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>인라인 코드

다음에 대한 예제입니다 `in-line code`.

## <a name="blockquotes"></a>Blockquotes

> 가뭄이 천만 년 동안 지속되고 공룡의 지배는 오래 전에 끝났습니다. Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight. In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.

## <a name="images"></a>이미지

### <a name="static-image"></a>정적 이미지

![this is the alt text](./media/AzRMS_elements.png)

### <a name="linked-image"></a>연결된 이미지

[![alt text for linked image](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>애니메이션 gif

![animated gif](./media/hololens.gif)

## <a name="alerts"></a>경고

### <a name="note"></a>참고

> [!NOTE]
> This is NOTE

### <a name="warning"></a>경고

> [!WARNING]
> This is WARNING

### <a name="tip"></a>팁

> [!TIP]
> This is TIP

### <a name="important"></a>중요

> [!IMPORTANT]
> This is IMPORTANT

## <a name="videos"></a>동영상

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms 확장

### <a name="button"></a>단추

> [!div class="button"]
[button links](/rights-management)

### <a name="selector"></a>선택기

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>단계별

>[!div class="step-by-step"]
[이전](https://www.example.com)
[다음](https://www.example.com)