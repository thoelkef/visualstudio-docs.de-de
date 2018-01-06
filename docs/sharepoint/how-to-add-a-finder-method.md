---
title: "Vorgehensweise: hinzufügen eine Finder-Methode | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b7594c650c1492b16e784ec649de6e66d1e6ec33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-finder-method"></a>Gewusst wie: Hinzufügen einer Finder-Methode
  Damit kann der Business Data Connectivity-Dienst, um eine Liste der Entitäten in einem Webpart oder einer Liste anzuzeigen, müssen Sie erstellen eine *Finder* Methode. Eine Finder-Methode ist eine besondere Methode, die eine Auflistung von Instanzen der Entität zurückgibt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Erstellen eine Finder-Methode  
  
1.  Wählen Sie eine Entität, auf dem BDC-Designer.  
  
     Weitere Informationen finden Sie unter [wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **BDC-Methodendetails**.  
  
     Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu den **BDC-Methodendetails** Fenster finden Sie unter [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der **Hinzufügen einer Methode** wählen **Finder-Methode erstellen**.  
  
     Visual Studio fügt eine Methode, einen Rückgabeparameter und ein Typdeskriptor.  
  
4.  Konfigurieren Sie den Typdeskriptor als Auflistung Entitätstypdeskriptor. Weitere Informationen zur Vorgehensweise beim Erstellen der Auflistung Entitätstypdeskriptor finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors eines Parameters](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Sie müssen nicht diesen Schritt ausführen, wenn Sie die Entität eine bestimmten Finder-Methode hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der bestimmten Finder-Methode definiert.  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü der Dienstcodedatei, die generiert wurde für die Entität, und wählen Sie dann **Code anzeigen**. Weitere Informationen zu Service-Codedatei, finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Fügen Sie Code hinzu, um Finder-Methode. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft Daten aus einer Datenquelle ab.  
  
    -   Gibt eine Liste der Entitäten an den BDC-Dienst zurück.  
  
     Das folgende Beispiel gibt eine Auflistung von `Contact` Entitäten mithilfe von Daten aus der AdventureWorks-Beispieldatenbank für SQL Server.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert, der die `ServerName` Feld mit dem Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Vorgehensweise: hinzufügen eine bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Vorgehensweise: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Vorgehensweise: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  