---
title: 'Vorgehensweise: Hinzufügen eine Updater-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 435674325acdb8b415f0a706f3bca8753d704160
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864162"
---
# <a name="how-to-add-an-updater-method"></a>Vorgehensweise: Hinzufügen einer Updater-Methode
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
 [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)   
 [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
