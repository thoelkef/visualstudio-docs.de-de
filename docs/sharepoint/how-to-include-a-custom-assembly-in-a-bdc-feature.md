---
title: 'Vorgehensweise: Einfügen einer benutzerdefinierte Assembly in eine BDC-Funktion | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4effb22f85ed7328a121340124f43b24b09e0ddc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870661"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion
  Das Projekt kann aus anderen Projekten in der gleichen Projektmappe auf Assemblys verweisen. Allerdings müssen Sie diese Assemblys auch das Feature-Datei des Projekts hinzufügen, mit der **weisen referenzierten Assemblys, LobSystems** Dialogfeld.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Um eine benutzerdefinierte Assembly in einem Business Data Connectivity (BDC)-Feature einzuschließen.
  
1.  In **Projektmappen-Explorer**, wählen Sie den Ordner mit dem BDC-Modell.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
3.  In der **Eigenschaften** Fenster, wählen Sie die **Assemblys** -Eigenschaft, und klicken Sie dann die Schaltfläche (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).  
  
     Die **weisen referenzierten Assemblys, LobSystems** Dialogfeld wird angezeigt.  
  
4.  In der **wählen Sie eine Assembly** Liste, und wählen Sie die benutzerdefinierte Assembly.  
  
    > [!NOTE]  
    >  Assemblys werden nur in der **weisen referenzierten Assemblys, LobSystems** im Dialogfeld, wenn Sie einen Verweis auf das Projekt hinzugefügt haben, die die Assembly enthält. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen oder Entfernen von verweisen mithilfe des Dialogfelds "Verweis" hinzufügen "](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  In der **Verweiseigenschaften** gruppieren, öffnen Sie die für die angezeigte Liste der **LobSystem-Bereich** -Eigenschaft, wählen Sie die LOB-System, der die Methoden, die die benutzerdefinierte Assembly, und wählen Sie dann die **OK**  Schaltfläche.  
  
    > [!NOTE]  
    >  Um Code in der benutzerdefinierten Assembly zu debuggen, müssen Sie die Assembly dem Lösungspaket hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integragte Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
