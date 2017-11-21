---
title: "Vorgehensweise: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0ae7190d0b55dec593e8d9f7c20542d5a7d5bc6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt
  Sie können anpassen, Paket und ein Business Data Connectivity (BDC)-Modell erneut bereit, mit Visual Studio die Modelldatei (.bdcm auf) auf jedem SharePoint-Farm-Projekt hinzufügen. Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Eine BDC-Modelldatei zu einem SharePoint-Projekt hinzufügen  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Ordner für eine SharePoint-Projekt.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **vorhandenes Element hinzufügen**.  
  
3.  In der **vorhandenes Element hinzufügen** (Dialogfeld), navigieren Sie zum Speicherort der Modell-Definitionsdatei, die Sie verwenden möchten, fügen Sie dem Projekt hinzu, wählen die Datei, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Wenn das Modell keine *Line of Business (LOB)-System vom Typ .NET Framework-Assembly*, **Hinzufügen von .NET Framework-Assembly LobSystem** Dialogfeld wird geöffnet.  
  
4.  Wenn das Dialogfeld angezeigt wird, führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn Sie benutzerdefinierten Code schreiben und verwenden Sie einen Designer, um die Metadaten für die importierte Modelle zu definieren, wählen möchten die **Ja** Schaltfläche, nennen Sie das System, und wählen Sie dann die **OK** Schaltfläche.  
  
    -   Wählen Sie andernfalls die **keine** aus, und klicken Sie dann die **OK** Schaltfläche.  
  
     Die **Business Data Connectivity-Modell** Element wird dem Projekt hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei lokalisierten Namen, Eigenschaften und Berechtigungen angeben.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  