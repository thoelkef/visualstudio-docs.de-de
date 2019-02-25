---
title: Erstellen eines Business Data Connectivity-Modells | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4873085a4e4508b40b866eee79e79f624f3c01d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605730"
---
# <a name="create-a-business-data-connectivity-model"></a>Erstellen eines Business Data Connectivity-Modells
  Sie können ein Business Data Connectivity (BDC)-Modell erstellen oder Anpassen ein vorhandenes BDC-Modell mithilfe von Visual Studio. Jede SharePoint-Projekt kann nur ein Modell enthalten. Weitere Informationen finden Sie unter [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Erstellen eines neuen Modells
 Um ein neues Modell zu erstellen, erstellen eine **Business Data Connectivity-Modells** oder zum Hinzufügen von einer **Business Data Connectivity-Modells** Elements an eine **leeres SharePoint-Projekt**.

> [!NOTE]
>  Sie benötigen [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] auf Ihrem Computer installiert.

 Visual Studio hinzugefügt dem Projekt einen Ordner. Dieser Ordner enthält den Namen, den Sie, für angeben die **Business Data Connectivity-Modells** Element in der **neues Element hinzufügen** Dialogfeld. Wenn Sie ein neues erstellen **Business Data Connectivity-Modells** Visual Studio-Projekt dem Ordner den Namen **BdcModel1**.

 Visual Studio fügt die folgenden Dateien in den neuen Ordner:

|Datei|Beschreibung|
|----------|-----------------|
|Modelldefinitionsdatei|Enthält XML, die definiert, die Entitäten, Methoden, Systemobjekte Line of Business (LOB) und anderen Metadaten, die das Modell beschreibt.<br /><br /> Ändern Sie die Metadaten in dieser Datei mit dem BDC-Designer, **BDC-Explorer**, **BDC-Methodendetails** Fenster und **Eigenschaften** Fenster.|
|Entität Authentifizierungsdienst-Codedatei|Enthält Methoden, die abrufen, aktualisieren und Löschen von Instanzen der Standardentität.|

 Um die Eigenschaften einer Entität zu definieren, bearbeiten Sie die Codedatei "Entity" ein. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Zum Abrufen, aktualisieren und Löschen von Instanzen einer Entität, fügen Sie Code hinzu, auf die Entität Authentifizierungsdienst-Codedatei. Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).

 Beim Kompilieren des Projekts erstellt Visual Studio eine Assembly an. Stellen Sie sicher, dass Sie keine weiteren Elemente nicht hinzufügen, um das Projekt, das die Projektassembly Code hinzu (z. B.: eine **sequenziellen Workflow** Element oder ein **Webpart** Element). Der Code für dieses Element wird nicht ausgeführt werden, wenn Sie die Lösung bereitgestellt werden, da das Lösungspaket dem globalen Assemblycache nicht die Assembly kopiert.  Das Lösungspaket wird die Assembly mit der BDC-Datenbank in SharePoint nur bereitstellt.

> [!NOTE]
>  Visual Studio kopiert die Assembly in beide Speicherorte auf dem lokalen Computer, wenn Sie das Debuggen des Projekts.

## <a name="add-an-existing-model"></a>Fügen Sie ein vorhandenes Modell hinzu.
 Sie können ein Modell importieren, die mit anderen Tools wie SharePoint Designer erstellt wurde. Sie können auch ein vorhandenes Modell zu Ihrem Projekt in den folgenden Situationen zu importieren:

- Um ein Modell anzupassen, die bereits mit einer SharePoint-Serverfarm bereitgestellt wird.

- Packen und Bereitstellen eines vorhandenen Modells auf mehrere SharePoint-Serverfarmen.

  In beiden Fällen die LOB-Systeme, die definiert, die im Modell, das Sie importieren, sind nicht betroffen und werden weiterhin wie erwartet funktionieren. Um ein vorhandenes Modell zu einer SharePoint-Projekt hinzuzufügen, verwenden Sie den Visual Studio **vorhandenes Element hinzufügen** Dialogfeld. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eine vorhandene BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Sie können ein LOB-System von .NET Framework-Assembly des Typs dem importierten Modell hinzufügen, indem Sie eine Option in der **Hinzufügen von .NET Framework-Assembly LobSystem**. Dadurch können Sie benutzerdefinierten Code schreiben und verwenden einen Designer, um die Metadaten für die importierte Modelle zu definieren.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)|Erfahren Sie, wie Sie ein neues BDC-Modell zu erstellen.|
|[Vorgehensweise: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Erfahren Sie, wie Sie ein vorhandenes Modell in einem SharePoint-Projekt zu importieren.|
|[Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Beschreibt, wie Zeichenfolgen, die zusammengeführt werden mit darin enthaltenen Modellmetadaten bereitgestellt werden, wenn das Modell von einem Webpart oder einer Webseite genutzt wird.|
|[Vorgehensweise: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Erfahren Sie, wie die Funktion eine benutzerdefinierte Assembly einschließt.|
