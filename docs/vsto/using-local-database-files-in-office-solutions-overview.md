---
title: Verwenden Sie lokaler Datenbankdateien in Office Solutions (Übersicht)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645536"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Verwenden Sie lokaler Datenbankdateien in Office Solutions (Übersicht)
  Sie können eine Datenbankdatei, z. B. eine SQL Server Express einschließen (*mdf*) Datei oder ein Microsoft Office Access (*MDB*) Datei, in der Office-Projektmappe. Dadurch kann Endbenutzer eine lokale Datenbank in Situationen, in denen Verwendung einer zentralen Datenbank nicht erforderlich, z. B. in einer lokalen inventarlösung ist, die auf nur einem einzelnen Computer verwendet wird.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importieren Sie die Datenbankdatei in ein Projekt.
 Um die Datenbankdatei in Ihr Projekt zu importieren, verwenden die **Assistenten zur Datenquellenkonfiguration** auf eine Datenquelle basierend auf der Datenbankdatei erstellen. Der Assistent fügt die Datenbankdatei und ein typisiertes Dataset zu Ihrem Projekt hinzu.

## <a name="deploy-the-database-file"></a>Bereitstellen der Datenbankdatei
 Die **Assistenten zur Datenquellenkonfiguration** einen relativen Pfad verwendet, um Verbindungen mit der lokalen Datenbankdatei zu erstellen. Dadurch können Sie die Lösung von einem Computer in ein anderes kopiert wird, wenn Sie die relativen Positionen von die Dateien verwalten.

 Wenn Sie Ihre Lösung auf einem Server bereitstellen, und klicken Sie dann das Dokument an alle Endbenutzer verteilen, müssen Sie auch manuell die Datenbankdatei zu verteilen und installieren Sie es in der gleichen Position relativ zu dem Dokument. Dies bedeutet, dass der Endbenutzer auf dem Computer, das Dokument an einem neuen Speicherort verschieben kann, es sei denn, er auch die Datei verschiebt.

## <a name="local-database-files-and-caching-the-dataset"></a>Lokaler Datenbankdateien und die Zwischenspeicherung von Datasets
 In Projektmappen auf Dokumentebene für Microsoft Office Excel und Microsoft Office Word können Sie Datasets im Dokument zwischenspeichern, indem Sie die Dataset-Instanz mit dem Attribut <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Beim Hinzufügen der Datei zu Ihrem Projekt durch Verwendung der **Assistenten zur Datenquellenkonfiguration**, ein typisiertes Dataset wird automatisch zu Ihrem Projekt hinzugefügt. Es ist selten notwendig, anzuwendende <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> auf dieses Dataset, da die Daten bereits lokal auf dem Computer des Benutzers vorhanden ist. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).

## <a name="see-also"></a>Siehe auch
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
- [Zwischenspeichern von Daten](../vsto/caching-data.md)
