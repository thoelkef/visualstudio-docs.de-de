---
title: 'Vorgehensweise: Hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa799e54f2fc8be22b78eca837d6aee2e683b1d3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863902"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt
  Sie können anpassen, Verpacken und erneutes Bereitstellen ein Business Data Connectivity (BDC)-Modells mithilfe von Visual Studio zum Hinzufügen der Modelldatei (*.bdcm*) auf jedem SharePoint-Farm-Projekt. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Eine BDC-Modelldatei zu einem SharePoint-Projekt hinzufügen  
  
1. In **Projektmappen-Explorer**, wählen Sie den Ordner für eine SharePoint-Projekt.  
  
2. Wählen Sie auf der Menüleiste **Projekt** > **vorhandenes Element hinzufügen**.  
  
3. In der **vorhandenes Element hinzufügen** wechseln zum Speicherort der die Modelldefinitionsdatei, die Sie verwenden möchten, fügen Sie Ihrem Projekt hinzu, wählen Sie die Datei, und wählen Sie im Dialogfeld die **hinzufügen** Schaltfläche.  
  
    Wenn das Modell zu definieren, keine *Line of Business (LOB)-System vom Typ .NET Assembly*, **Hinzufügen von .NET Framework-Assembly LobSystem** Dialogfeld wird geöffnet.  
  
4. Wenn Sie das Dialogfeld angezeigt wird, führen Sie einen der folgenden Schritte aus:  
  
   - Sollten Sie benutzerdefinierten Code schreiben und verwenden einen Designer, um die Metadaten für die importierte Modelle zu definieren, wählen die **Ja** Schaltfläche nennen Sie das System, und wählen Sie dann die **OK** Schaltfläche.  
  
   - Wählen Sie andernfalls die **keine** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Business Data Connectivity-Modells** Element wird dem Projekt hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
