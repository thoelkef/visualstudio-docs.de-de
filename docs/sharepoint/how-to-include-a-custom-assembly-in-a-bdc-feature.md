---
title: "Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5916da8b7aa5018824ffe8040e7184fe6d1bf31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion
  Das Projekt kann aus anderen Projekten in derselben Projektmappe Assemblys verweisen. Sie müssen jedoch diese Assemblys die Feature-Datei des Projekts hinzufügen, mit der **weisen referenzierten Assemblys, LobSystems** (Dialogfeld).  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Hinzufügen eine benutzerdefinierte Assembly in einem Business Data Connectivity (BDC)-Funktion  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Ordner mit dem BDC-Modell.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.  
  
3.  In der **Eigenschaften** Fenster, wählen Sie die **Assemblys** -Eigenschaft und dann die Schaltfläche mit den Auslassungspunkten (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).  
  
     Die **weisen referenzierten Assemblys, LobSystems** Dialogfeld wird angezeigt.  
  
4.  In der **wählen Sie eine Assembly** wählen Sie die benutzerdefinierte Assembly.  
  
    > [!NOTE]  
    >  Assemblys werden nur der **weisen referenzierten Assemblys, LobSystems** (Dialogfeld), wenn Sie einen Verweis zum Projekt hinzugefügt haben, die die Assembly enthält. Weitere Informationen finden Sie unter [wie: Hinzufügen oder Entfernen von verweisen mithilfe des Dialogfelds der hinzufügen-Verweis](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  In der **Verweiseigenschaften** gruppieren, öffnen Sie die Liste, die für die **LobSystem Bereich** -Eigenschaft, wählen Sie die LOB-System der Methoden, die die benutzerdefinierte Assembly, und wählen Sie dann die **OK**  Schaltfläche.  
  
    > [!NOTE]  
    >  Zum Debuggen von Code in einer benutzerdefinierten Assembly müssen Sie die Assembly zum Lösungspaket hinzufügen. Weitere Informationen finden Sie unter [wie: Hinzufügen und Entfernen zusätzlicher Assemblys](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei lokalisierten Namen, Eigenschaften und Berechtigungen angeben.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Vorgehensweise: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  