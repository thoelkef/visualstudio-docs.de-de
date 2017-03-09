---
title: "Gewusst wie: Konfigurieren von Projekten f&#252;r Zielplattformen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64 Bit [Visual Studio]"
  - "64-Bit-Anwendungen [Visual Studio]"
  - "64-Bit-Programmierung [Visual Studio]"
  - "CPUs, Zielspezifisch"
  - "Plattformen, Spezifische CPUs für"
  - "Projekteigenschaften [Visual Studio], Plattformen für"
  - "Projekteinstellungen [Visual Studio], Plattformen für"
  - "Projekte [Visual Studio], Plattformen für"
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Konfigurieren von Projekten f&#252;r Zielplattformen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ermöglicht es Ihnen, die Anwendungen für unterschiedliche Zielplattformen einzurichten, einschließlich 64\-Bit\-Plattformen.  Weitere Informationen zur Unterstützung von 64\-Bit\-Plattformen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] finden Sie unter [64\-Bit\-Anwendungen](../Topic/64-bit%20Applications.md).  
  
## Festlegen von Zielplattformen mit dem Konfigurations\-Manager  
 Mit dem **Konfigurations\-Manager** können Sie für ein Projekt schnell eine neue Zielplattform hinzufügen.  Wenn Sie eine der in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthaltenen Plattformen auswählen, werden die Projekteigenschaften geändert, um das Projekt unter Berücksichtigung der ausgewählten Plattform zu erstellen.  
  
#### So konfigurieren Sie ein Projekt für eine 64\-Bit\-Plattform  
  
1.  Wählen Sie auf der Menüleiste die Option **Erstellen** und dann **Konfigurations\-Manager** aus.  
  
2.  Wählen Sie in der Liste **Aktive Projektmappenplattform** eine 64\-Bit\-Plattform als Zielplattform für die Projektmappe aus, und wählen Sie dann die Schaltfläche **Schließen**.  
  
    1.  Wählen Sie **Neu**, wenn die gewünschte Plattform nicht in der Liste **Aktive Projektmappenplattform** angezeigt wird.  
  
         Das Dialogfeld **Neue Projektmappenplattform** wird angezeigt.  
  
    2.  Wählen Sie in der Liste **Neue Plattform eingeben oder auswählen x64** aus.  
  
        > [!NOTE]
        >  Wenn Sie die Konfiguration neu benennen, müssen Sie möglicherweise die Einstellungen für die gewünschte Zielplattform im **Projekt\-Designer** konfigurieren.  
  
    3.  Wenn Sie die Einstellungen aus der aktuellen Plattformkonfiguration kopieren möchten, wählen Sie diese aus, und wählen Sie dann die Schaltfläche **OK** aus.  
  
 Es werden die Eigenschaften für alle Projekte mit der 64\-Bit\-Plattform als Zielplattform aktualisiert, und der nächste Build des Projekts wird für 64\-Bit\-Plattformen optimiert.  
  
## Festlegen von Zielplattformen im Projekt\-Designer  
 Mit dem Projekt\-Designer können Sie ebenfalls unterschiedliche Zielplattformen für Ihr Projekt festlegen.  Wenn Sie die gewünschte Zielplattform nicht in der Liste im Dialogfeld **Neue Projektmappenplattform** auswählen können, können Sie eine benutzerdefinierte Konfiguration erstellen und benennen und die Einstellungen für die gewünschte Zielplattform im **Projekt\-Designer** konfigurieren.  
  
 Die für diese Aufgabe erforderlichen Schritte sind je nach Programmiersprache unterschiedlich.  Weitere Informationen finden Sie unter den folgenden Links:  
  
-   Informationen zu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekten finden Sie unter [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Informationen zu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Projekten finden Sie unter [Seite "Erstellen", Projekt\-Designer \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Informationen zu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projekten finden Sie unter [\/clr \(Common Language Runtime\-Kompilierung\)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
## Siehe auch  
 [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md)   
 [\/platform \(Specify Output Platform\)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [64\-Bit\-Anwendungen](../Topic/64-bit%20Applications.md)   
 [Visual Studio\-IDE\-64\-Bit\-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)