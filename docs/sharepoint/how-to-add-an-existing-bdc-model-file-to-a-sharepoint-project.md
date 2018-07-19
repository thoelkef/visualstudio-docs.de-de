---
title: 'Vorgehensweise: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f7508cf8c66343894c16da7ff840bd275abb65c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755897"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Gewusst wie: hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt
  Sie können anpassen, Verpacken und erneutes Bereitstellen ein Business Data Connectivity (BDC)-Modells mithilfe von Visual Studio zum Hinzufügen der Modelldatei (*.bdcm*) auf jedem SharePoint-Farm-Projekt. Weitere Informationen finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Eine BDC-Modelldatei zu einem SharePoint-Projekt hinzufügen  
  
1.  In **Projektmappen-Explorer**, wählen Sie den Ordner für eine SharePoint-Projekt.  
  
2.  Wählen Sie auf der Menüleiste **Projekt** > **vorhandenes Element hinzufügen**.  
  
3.  In der **vorhandenes Element hinzufügen** wechseln zum Speicherort der die Modelldefinitionsdatei, die Sie verwenden möchten, fügen Sie Ihrem Projekt hinzu, wählen Sie die Datei, und wählen Sie im Dialogfeld die **hinzufügen** Schaltfläche.  
  
     Wenn das Modell zu definieren, keine *Line of Business (LOB)-System vom Typ .NET Assembly*, **Hinzufügen von .NET Framework-Assembly LobSystem** Dialogfeld wird geöffnet.  
  
4.  Wenn Sie das Dialogfeld angezeigt wird, führen Sie einen der folgenden Schritte aus:  
  
    -   Sollten Sie benutzerdefinierten Code schreiben und verwenden einen Designer, um die Metadaten für die importierte Modelle zu definieren, wählen die **Ja** Schaltfläche nennen Sie das System, und wählen Sie dann die **OK** Schaltfläche.  
  
    -   Wählen Sie andernfalls die **keine** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Business Data Connectivity-Modells** Element wird dem Projekt hinzugefügt.  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Gewusst wie: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Gewusst wie: Einfügen einer benutzerdefinierte Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
 
