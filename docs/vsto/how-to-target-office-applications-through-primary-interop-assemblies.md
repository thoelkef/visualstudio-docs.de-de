---
title: 'Vorgehensweise: Ziel Office-Anwendungen durch primäre Interopassemblys'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262511"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Vorgehensweise: Ziel Office-Anwendungen durch primäre Interopassemblys
  Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die primären Interopassemblys (PIAs) von Microsoft Office hinzu, die zum Erstellen des Projekts erforderlich sind. Verweise auf andere PIAs müssen in den folgenden Szenarien hinzugefügt werden:  
  
-   Sie möchten Funktionen anderer Microsoft Office-Anwendungen im Projekt verwenden. Sie möchten z. B. Features von Microsoft Office Excel in einem Projekt für Microsoft Office Word verwenden.  
  
-   Sie möchten Microsoft Office-Anwendungen automatisieren, die nicht über dedizierte Projekte in Visual Studio verfügen, z. B. Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>So fügen Sie einen Verweis auf eine primäre Interopassembly hinzu  
  
1.  Öffnen Sie das Office-Projekt, und wählen Sie den Projektnamen im **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen** .  
  
3.  Auf der **Framework** Registerkarte, wählen Sie die PIA, Sie in möchten, der **Komponentenname** Liste. Weitere Informationen zu den verfügbaren primären Interop-Assemblys für Microsoft Office, finden Sie unter [primären Interopassemblys von Office](../vsto/office-primary-interop-assemblies.md).  
  
     Wenn das Projekt als Zielversion der [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher, die **Interoptypen** -Eigenschaft für der Assemblyverweis verweist auf festgelegt ist **"true"** standardmäßig. Mit dieser Einstellung erfordert die Lösung keine PIA auf Endbenutzercomputern. Weitere Informationen finden Sie unter [entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  In Office-Projekten mit Verweisen auf Office-PIAs immer Hinzufügen der **.NET** auf der Registerkarte die **Verweis hinzufügen** Dialogfeld statt über das **COM** Registerkarte. Weitere Informationen finden Sie unter [primären Interopassemblys von Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Klicken Sie auf **OK**.  
  
     Der Assemblyname wird in der **Verweise** Ordner **Projektmappen-Explorer**.  
  
## <a name="see-also"></a>Siehe auch  
 [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Vorgehensweise: Installieren von Office primary Interop-Assemblys](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  