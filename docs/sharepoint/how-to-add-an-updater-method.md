---
title: 'Vorgehensweise: hinzufügen eine Updater-Methode | Microsoft-Dokumentation'
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
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4d50180173673b4999c18b8980c682d79637bd3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951417"
---
# <a name="how-to-add-an-updater-method"></a>Gewusst wie: hinzufügen eine Updater-Methode
  Sie können Benutzern ermöglichen, aktualisieren Sie Geschäftsdaten in einer externen SharePoint-Liste durch das Erstellen einer *Updater* Methode. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-an-updater-method"></a>Zum Erstellen einer Updater-Methode  
  
1. Wählen Sie eine Entität, auf dem BDC-Designer.  
  
2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.  
  
    Das BDC-Methodendetails-Fenster wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. In der **Hinzufügen einer Methode** wählen **Updater-Methode erstellen**.  
  
    Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden im BDC-Methodendetails angezeigt.  
  
   - Eine Methode mit dem Namen **Update**.  
  
   - Ein Eingabeparameter für die Methode.  
  
   - Ein Typdeskriptor für den Parameter. Standardmäßig verwendet Visual Studio den Entitätstypdeskriptor, die Sie definiert, für die Finder-Methode (z. B.: Wenden Sie sich an).  
  
   - Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
   > [!NOTE]  
   >  Wenn der Bezeichner des Entitätstyps ein Feld in einer Datenbanktabelle, die nicht automatisch generiert wird darstellt, legen Sie die **Pre-Updater-Feld** Eigenschaft **"true"**.  
  
4. In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü des der Authentifizierungsdienst-Codedatei, die generiert wurde für die Entität aus, und wählen Sie dann **Ansichtscode**.  
  
    Die Entität Authentifizierungsdienst-Codedatei wird geöffnet, der **Code-Editor**. Weitere Informationen zu dieser Datei finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Fügen Sie Code hinzu, die Update-Methode, um Daten zu aktualisieren. Das folgende Beispiel aktualisiert die Informationen für einen Kontakt in der AdventureWorks-Beispieldatenbank für SQL Server.  
  
   > [!NOTE]  
   >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.  
  
    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]  
  
## <a name="see-also"></a>Siehe auch
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: hinzufügen eine Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: hinzufügen eine bestimmte Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: hinzufügen eine Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: hinzufügen eine Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Gewusst wie: hinzufügen eine Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
 
