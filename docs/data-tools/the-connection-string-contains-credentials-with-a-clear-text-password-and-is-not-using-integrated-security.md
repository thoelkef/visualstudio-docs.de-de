---
title: Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b9c807266182b419dc0967288715a187042f83b1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586171"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.

Möchten Sie die Verbindungszeichenfolge mit vertraulichen Informationen in der aktuellen DBML-Datei und in den Anwendungskonfigurationsdateien speichern?  Klicken Sie auf **Nein**, um die Verbindungszeichenfolge ohne die vertraulichen Informationen zu speichern.

Beim Arbeiten mit Datenverbindungen, die vertrauliche Informationen enthalten (in der Verbindungszeichenfolge enthaltene Kennwörter) haben Sie die Option, die Verbindungszeichenfolge mit den vertraulichen Informationen oder ohne diese in der DBML-Datei und der Anwendungskonfigurationsdatei des Projekts zu speichern.

> [!WARNING]
> Wenn Sie die Eigenschaft **Anwendungseinstellungen** der **Verbindungseigenschaften** auf **False** festlegen, wird das Kennwort der DBML-Datei hinzugefügt.

## <a name="save-options"></a>Speicheroptionen

- Um die Verbindungs Zeichenfolge mit den vertraulichen Informationen zu speichern, wählen Sie **Ja**aus.

   Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert. Die Verbindungszeichenfolge enthält die vertraulichen Informationen als Klartext. Die vertraulichen Informationen sind nicht in der DBML-Datei enthalten.

- Wenn Sie die Verbindungs Zeichenfolge ohne vertrauliche Informationen speichern möchten, wählen Sie **Nein**aus.

   Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert, jedoch ohne das Kennwort.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
