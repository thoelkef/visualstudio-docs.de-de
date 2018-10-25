---
title: 'Vorgehensweise: hinzufügen eine Creator-Methode | Microsoft-Dokumentation'
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
ms.openlocfilehash: a8aa49416a826e5100932b4741d3e536a9d2f37d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897341"
---
# <a name="how-to-add-a-creator-method"></a>Gewusst wie: hinzufügen eine Creator-Methode
  Eine Creator-Methode fügt neue Daten an die Datenquelle einer Entität. Der Business Data Connectivity (BDC)-Dienst ruft diese Methode auf, wenn Benutzer die **neues Element** Schaltfläche der **Menüband** einer Liste, die für das Modell basiert. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Zum Hinzufügen einer Creator-Methode  
  
1. Auf der **BDC-Designer**, wählen Sie eine Entität.  
  
2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** >**BDC-Methodendetails**.  
  
    Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster, finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. In der **Hinzufügen einer Methode** wählen **Creator-Methode erstellen**.  
  
    Visual Studio fügt die folgenden Elemente für das Modell, und diese Elemente werden angezeigt, der **BDC-Methodendetails** Fenster.  
  
   - Eine Methode namens **erstellen**.  
  
   - Ein Eingabeparameter für die Methode.  
  
   - Ein Rückgabeparameter für die Methode.  
  
   - Geben Sie die Deskriptoren für die Parameter.  
  
   - Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü des der Authentifizierungsdienst-Codedatei, die generiert wurde für die Entität aus, und wählen Sie dann **Ansichtscode**.  
  
    Die Entität Authentifizierungsdienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Authentifizierungsdienst-Codedatei, finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Fügen Sie Code, der Creator-Methode, die Daten der Datenquelle hinzugefügt. Das folgende Beispiel fügt einen Kontakt mit der AdventureWorks-Beispieldatenbank für SQL Server.  
  
   > [!NOTE]  
   >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.  
  
    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Siehe auch
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: hinzufügen eine bestimmte Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  
