---
title: 'Vorgehensweise: Hinzufügen eine Deleter-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7a486ea4a448cb30b64631589f003854e8b1b40
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644392"
---
# <a name="how-to-add-a-deleter-method"></a>Vorgehensweise: Hinzufügen einer Deleter-Methode
  Sie können die Benutzer, einen Datensatz aus einer externen Liste auf einer SharePoint-Website zu löschen, durch das Hinzufügen einer Deleter-Methode für das Modell aktivieren. Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Erstellen eine Deleter-Methode

1. Auf der **BDC-Designer**, wählen Sie eine Entität.

2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.

    Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu diesem Fenster finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).

3. In der **Hinzufügen einer Methode** wählen **Erstellen einer Deleter-Methode**.

    Visual Studio fügt die folgenden Elemente für das Modell. Diese Elemente werden angezeigt, der **BDC-Methodendetails** Fenster.

   - Eine Methode namens **löschen**.

   - Ein Eingabeparameter für die Methode.

   - Ein Typdeskriptor für den Parameter.

   - Eine Methodeninstanz für die Methode.

     Weitere Informationen finden Sie unter [entwerfen ein Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

4. In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü des der Authentifizierungsdienst-Codedatei, die generiert wurde für die Entität aus, und wählen Sie dann **Ansichtscode**.

    Die Entität Authentifizierungsdienst-Codedatei wird im Code-Editor geöffnet. Weitere Informationen zu der Entität Authentifizierungsdienst-Codedatei, finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Fügen Sie Code hinzu, um die Deleter-Methode, die einen Datensatz zu löschen. Das folgende Beispiel löscht einen Eintrag aus einem Auftrag mit der AdventureWorks-Beispieldatenbank für SQL Server.

   > [!NOTE]
   >  Die Methode in diesem Beispiel verwendet zwei Eingabeparameter an.

   > [!NOTE]
   >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>Siehe auch
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)
