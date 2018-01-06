---
title: "Vorgehensweise: Office-Anwendungen durch primäre Interopassemblys Ziel | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: bf714645f126f8a6f5e8aaca3ee6a2721bfe0a71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Verweisen auf Office-Anwendungen durch primäre Interopassemblys
  Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die primären Interopassemblys (PIAs) von Microsoft Office hinzu, die zum Erstellen des Projekts erforderlich sind. Verweise auf andere PIAs müssen in den folgenden Szenarien hinzugefügt werden:  
  
-   Sie möchten Funktionen anderer Microsoft Office-Anwendungen im Projekt verwenden. Sie möchten z. B. Features von Microsoft Office Excel in einem Projekt für Microsoft Office Word verwenden.  
  
-   Sie möchten Microsoft Office-Anwendungen automatisieren, die nicht über dedizierte Projekte in Visual Studio verfügen, z. B. Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>So fügen Sie einen Verweis auf eine primäre Interopassembly hinzu  
  
1.  Öffnen Sie das Office-Projekt, und wählen Sie den Projektnamen im **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen** .  
  
3.  Auf der **Framework** Registerkarte, wählen Sie die PIA, Sie in möchten, der **Komponentenname** Liste. Weitere Informationen zu den verfügbaren primären Interop-Assemblys für Microsoft Office, finden Sie unter [Office Primary Interopassemblys](../vsto/office-primary-interop-assemblies.md).  
  
     Wenn das Projekt als Zielversion der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, die **Interoptypen** -Eigenschaft für der Assemblyverweis verweist auf festgelegt ist **"true"** standardmäßig. Mit dieser Einstellung erfordert die Lösung keine PIA auf Endbenutzercomputern. Weitere Informationen finden Sie unter [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  In Office-Projekten mit Verweisen auf Office-PIAs immer Hinzufügen der **.NET** auf der Registerkarte die **Verweis hinzufügen** Dialogfeld statt über das **COM** Registerkarte. Weitere Informationen finden Sie unter [Primäre Interop-Assemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Klicken Sie auf **OK**.  
  
     Der Assemblyname wird in der **Verweise** Ordner **Projektmappen-Explorer**.  
  
## <a name="see-also"></a>Siehe auch  
 [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  