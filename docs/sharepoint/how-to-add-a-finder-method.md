---
title: 'Vorgehensweise: hinzufügen eine Finder-Methode | Microsoft Docs'
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
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7773c2c81527e065652486eb851f3c27828bf76d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767131"
---
# <a name="how-to-add-a-finder-method"></a>Vorgehensweise: hinzufügen eine Finder-Methode
  Damit kann den Business Data Connectivity (BDC)-Dienst, um eine Liste der Entitäten in einem Webpart oder einer Liste anzuzeigen, müssen Sie erstellen eine *Finder* Methode. Eine Finder-Methode ist eine besondere Methode, die eine Auflistung von Instanzen der Entität zurückgibt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-finder-method"></a>Erstellen eine Finder-Methode  
  
1.  Auf der **BDC-Designer**, wählen Sie eine Entität.  
  
     Weitere Informationen finden Sie unter [wie: hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Wählen Sie in der Menüleiste **Ansicht** > **Weitere Fenster** > **BDC-Methodendetails**.  
  
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
  
  