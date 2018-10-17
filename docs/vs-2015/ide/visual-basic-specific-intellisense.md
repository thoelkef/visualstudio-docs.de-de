---
title: Visual Basic-spezifisches IntelliSense | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9d9d41b6b98396d253b810fb8ea9485a3d9e0df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239485"
---
# <a name="visual-basic-specific-intellisense"></a>Visual Basic-spezifisches IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Quellcode-Editor von Visual Basic stellt die folgenden IntelliSense-Features bereit:  
  
-   Tipps zur Syntax  
  
     In den Tipps zur Syntax wird die Syntax der Anweisung angezeigt, die Sie eintippen. Dies ist für Anweisungen wie [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1) nützlich.  
  
## <a name="automatic-completion"></a>Automatische Vervollständigung  
  
-   Vervollständigung unterschiedlicher Schlüsselwörter  
  
     Wenn Sie beispielsweise `goto` und ein Leerzeichen eingeben, zeigt IntelliSense eine Liste der definierten Bezeichnungen in einem Dropdownmenü. Andere unterstützte Schlüsselwörter sind unter anderem `Exit`, `Implements`, `Option` und `Declare`.  
  
-   Vervollständigung für `Enum` und `Boolean`  
  
     Wenn eine Anweisung auf ein Member einer Enumeration verweist, zeigt IntelliSense eine Liste der Member der `Enum`-Aufzählung. Wenn eine Anweisung auf `Boolean` verweist, zeigt IntelliSense ein Dropdownmenü mit TRUE und FALSE an.  
  
 Die Vervollständigung kann standardmäßig deaktiviert werden. Wählen Sie hierzu von der Eigenschaftenseite **Allgemein** im Ordner **Visual Basic** **Member automatisch auflisten** aus.  
  
 Sie können die Vervollständigung manuell aufrufen, indem Sie auf „Member auflisten“ oder „Wort vervollständigen“ klicken oder ALT+NACH-RECHTS-TASTE drücken. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>IntelliSense pro Zone  
 „IntelliSense pro Zone“ hilft Visual Basic-Entwicklern, die Anwendungen über [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bereitstellen müssen und durch Einstellungen für teilweise vertrauenswürdige Anwendungen eingeschränkt sind. Mithilfe dieser Funktion  
  
-   wird Ihnen ermöglicht, die Berechtigungen auszuwählen, mit der die Anwendung ausgeführt wird.  
  
-   werden APIs in der ausgewählten Zone in „Member auflisten“ als verfügbar angezeigt und APIs, die zusätzliche Berechtigungen erfordern, als nicht verfügbar angezeigt.  
  
 Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von IntelliSense](../ide/using-intellisense.md)



