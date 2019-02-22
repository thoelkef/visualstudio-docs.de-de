---
title: 'Vorgehensweise: Hinzufügen eine Creator-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c1596213b618ba67cd4bf1406f63c0754fd9b96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619315"
---
# <a name="how-to-add-a-creator-method"></a>Vorgehensweise: Hinzufügen einer Creator-Methode
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
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Vorgehensweise: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)
- [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)
