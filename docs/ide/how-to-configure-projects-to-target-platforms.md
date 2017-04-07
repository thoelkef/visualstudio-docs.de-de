---
title: "Vorgehensweise: Konfigurieren von Projekten für Zielplattformen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: c9ab9bf094a57baf4a309e3064cfcea9180dfebc
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-configure-projects-to-target-platforms"></a>Gewusst wie: Konfigurieren von Projekten für Zielplattformen
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Ihnen, die Anwendungen für unterschiedliche Zielplattformen einzurichten, einschließlich 64-Bit-Plattformen. Weitere Informationen zur Unterstützung von 64-Bit-Plattformen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finden Sie unter [64-Bit-Anwendungen](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Festlegen von Zielplattformen mit dem Konfigurations-Manager  
 Mit dem **Konfigurations-Manager** können Sie für ein Projekt schnell eine neue Zielplattform hinzufügen. Wenn Sie eine der in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthaltenen Plattformen auswählen, werden die Projekteigenschaften geändert, um das Projekt unter Berücksichtigung der ausgewählten Plattform zu erstellen.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>So konfigurieren Sie ein Projekt für eine 64-Bit-Plattform  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen**und dann **Konfigurations-Manager**aus.  
  
2.  Wählen Sie in der Liste **Aktive Projektmappenplattform** eine 64-Bit-Plattform als Zielplattform für die Projektmappe aus, und klicken Sie dann auf die Schaltfläche **Schließen**.  
  
    1.  Wählen Sie **Neu** aus, wenn die gewünschte Plattform nicht in der Liste **Aktive Projektmappenplattform** angezeigt wird.  
  
         Das Dialogfeld **Neue Projektmappenplattform** wird angezeigt.  
  
    2.  Wählen Sie in der Liste **Neue Plattform eingeben oder auswählen** **x64** aus.  
  
        > [!NOTE]
        >  Wenn Sie die Konfiguration neu benennen, müssen Sie möglicherweise die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.  
  
    3.  Wenn Sie die Einstellungen aus der aktuellen Plattformkonfiguration kopieren möchten, wählen Sie diese aus, und wählen Sie anschließend die Schaltfläche **OK** aus.  
  
 Es werden die Eigenschaften für alle Projekte mit der 64-Bit-Plattform als Zielplattform aktualisiert, und der nächste Build des Projekts wird für 64-Bit-Plattformen optimiert.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Festlegen von Zielplattformen im Projekt-Designer  
 Mit dem Projekt-Designer können Sie ebenfalls unterschiedliche Zielplattformen für Ihr Projekt festlegen. Wenn Sie die gewünschte Zielplattform nicht in der Liste im Dialogfeld **Neue Projektmappenplattform** auswählen können, können Sie eine benutzerdefinierte Konfiguration erstellen und benennen und die Einstellungen für die gewünschte Zielplattform im **Projekt-Designer** konfigurieren.  
  
 Die für diese Aufgabe erforderlichen Schritte sind je nach Programmiersprache unterschiedlich. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   Informationen zu -[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projekten finden Sie unter [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Informationen zu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekten finden Sie unter [Seite „Erstellen“, Projekt-Designer](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Informationen zu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekten finden Sie unter [/clr (Common Language Runtime-Kompilierung)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md)   
 [-platform (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64-Bit-Anwendungen](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)
