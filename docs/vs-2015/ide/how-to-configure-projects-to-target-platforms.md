---
title: 'Vorgehensweise: Konfigurieren von Projekten für Zielplattformen | Microsoft-Dokumentation'
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
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2e945a3a55f1ea4f9e68b96209e350c843324c30
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294514"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Gewusst wie: Konfigurieren von Projekten für Zielplattformen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ermöglicht es Ihnen, die Anwendungen für unterschiedliche Zielplattformen einzurichten, einschließlich 64-Bit-Plattformen. Weitere Informationen zur Unterstützung von 64-Bit-Plattformen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finden Sie unter [64-Bit-Anwendungen](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Festlegen von Zielplattformen mit dem Konfigurations-Manager  
 Mit dem **Konfigurations-Manager** können Sie für ein Projekt schnell eine neue Zielplattform hinzufügen. Wenn Sie eine der in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] enthaltenen Plattformen auswählen, werden die Projekteigenschaften geändert, um das Projekt unter Berücksichtigung der ausgewählten Plattform zu erstellen.  
  
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
  
-   Informationen zu -[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Projekten finden Sie unter [/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
-   Informationen zu [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Projekten finden Sie unter [Seite „Erstellen“, Projekt-Designer](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Informationen zu [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Projekten finden Sie unter [/clr (Common Language Runtime-Kompilierung)](http://msdn.microsoft.com/library/fec5a8c0-40ec-484c-a213-8dec918c1d6c).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md)   
 [-platform (C#-Compileroptionen)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04)   
 [64-Bit-Anwendungen](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)



