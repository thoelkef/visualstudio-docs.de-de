---
title: 'Vorgehensweise: Hinzufügen einer Deleter-Methode | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a0607bcd05fcb0d63fcc9bff40dfffeb2c45b8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-deleter-method"></a>Gewusst wie: Hinzufügen einer Deleter-Methode
  Sie können einen Endbenutzer So löschen Sie einen Datensatz aus einer externen Liste auf einer SharePoint-Website durch Hinzufügen einer *Deleter* Methode, um das Modell. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-deleter-method"></a>Erstellen eine Deleter-Methode  
  
1.  Wählen Sie eine Entität, auf dem BDC-Designer.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **Hinzufügen einer Methode** wählen **erstellen Sie eine Deleter-Methode**.  
  
     Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden der **BDC-Methodendetails** Fenster.  
  
    -   Eine Methode namens **löschen**.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für den Parameter.  
  
    -   Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü der Dienstcodedatei, die generiert wurde für die Entität, und wählen Sie dann **Code anzeigen**.  
  
     Die Entität Service-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Service-Codedatei, finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Fügen Sie Code auf die Deleter-Methode, einen Datensatz zu löschen. Das folgende Beispiel löscht einen Einzelposten aus einem Auftrag mit der AdventureWorks-Beispieldatenbank für SQL Server.  
  
    > [!NOTE]  
    >  Die Methode in diesem Beispiel verwendet zwei Eingabeparameter.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  