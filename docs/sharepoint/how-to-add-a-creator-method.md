---
title: 'Vorgehensweise: hinzufügen eine Creator-Methode | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0424c6561b063b17f384215021a1300122dcbb1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-creator-method"></a>Gewusst wie: Hinzufügen einer Creator-Methode
  Eine Creator-Methode fügt neue Daten an die Datenquelle einer Entität. Business Data Connectivity (BDC)-Dienst ruft diese Methode auf, wenn Benutzer die **neues Element** Schaltfläche auf dem Menüband eine Liste, die auf das Modell basiert. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Hinzufügen eine Creator-Methode  
  
1.  Wählen Sie eine Entität, auf dem BDC-Designer.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **Hinzufügen einer Methode** wählen **Creator-Methode erstellen**.  
  
     Visual Studio fügt die folgenden Elemente für das Modell, und diese Elemente werden der **BDC-Methodendetails** Fenster.  
  
    -   Eine Methode namens **erstellen**.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Geben Sie die Deskriptoren für die Parameter.  
  
    -   Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü der Dienstcodedatei, die generiert wurde für die Entität, und wählen Sie dann **Code anzeigen**.  
  
     Die Entität Service-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Service-Codedatei, finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Fügen Sie Code, der Ersteller-Methode, die Daten an die Datenquelle hinzugefügt. Im folgenden Beispiel wird die AdventureWorks-Beispieldatenbank für SQL Server einen Kontakt hinzugefügt.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  