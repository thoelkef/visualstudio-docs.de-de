---
title: 'Vorgehensweise: Hinzufügen eine Finder-Methode | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dc61db134063c1e300a2620f611d62497fffe6e1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608070"
---
# <a name="how-to-add-a-finder-method"></a>Vorgehensweise: Hinzufügen einer Finder-Methode
  Damit können den Business Data Connectivity (BDC)-Dienst, um eine Liste von Entitäten in einem Webpart oder einer Liste anzuzeigen, müssen Sie erstellen eine *Finder* Methode. Eine Finder-Methode ist eine besondere Methode, die eine Auflistung von Instanzen der Entität zurückgibt. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Erstellen eine Finder-Methode

1. Auf der **BDC-Designer**, wählen Sie eine Entität.

    Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **BDC-Methodendetails**.

    Die **BDC-Methodendetails** Fenster wird geöffnet. Weitere Informationen zu den **BDC-Methodendetails** Fenster finden Sie unter [BDC-Modell-Designtools Übersicht](../sharepoint/bdc-model-design-tools-overview.md).

3. In der **Hinzufügen einer Methode** wählen **Finder-Methode erstellen**.

    Visual Studio fügt eine Methode, einen Rückgabeparameter und ein Typdeskriptor.

4. Konfigurieren Sie den Typdeskriptor als Typdeskriptor eine Entity-Auflistung. Weitere Informationen zum Erstellen der Sammlung Entitätstypdeskriptor finden Sie unter [Vorgehensweise: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   >  Sie müssen nicht diesen Schritt ausführen, wenn Sie eine spezifische Finder-Methode für die Entität hinzugefügt haben. Visual Studio verwendet den Typdeskriptor, den Sie in der spezifische Finder-Methode definiert.

5. In **Projektmappen-Explorer**, öffnen Sie im Kontextmenü des der Authentifizierungsdienst-Codedatei, die generiert wurde für die Entität aus, und wählen Sie dann **Ansichtscode**. Weitere Informationen zu den Authentifizierungsdienst-Codedatei, finden Sie unter [erstellen ein Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Fügen Sie Code hinzu, um die Finder-Methode. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Ruft Daten aus einer Datenquelle ab.

   - Gibt eine Liste der Entitäten mit dem BDC-Dienst zurück.

     Das folgende Beispiel gibt eine Auflistung von `Contact` Entitäten durch Verwenden von Daten aus der AdventureWorks-Beispieldatenbank für SQL Server.

   > [!NOTE]
   >  Ersetzen Sie den Wert der `ServerName` Feld mit dem Namen Ihres Servers.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>Siehe auch
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Vorgehensweise: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Vorgehensweise: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)
- [Vorgehensweise: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)
- [Vorgehensweise: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)
