---
title: Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bcd459208529441022669e799e3c59b16b4ef682
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174074"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.

Möchten Sie die Verbindungszeichenfolge mit vertraulichen Informationen in der aktuellen DBML-Datei und in den Anwendungskonfigurationsdateien speichern?  Klicken Sie auf **keine** um die Verbindungszeichenfolge ohne die vertraulichen Informationen zu speichern.

Beim Arbeiten mit Datenverbindungen, die vertrauliche Informationen enthalten (in der Verbindungszeichenfolge enthaltene Kennwörter) haben Sie die Option, die Verbindungszeichenfolge mit den vertraulichen Informationen oder ohne diese in der DBML-Datei und der Anwendungskonfigurationsdatei des Projekts zu speichern.

> [!WARNING]
> Explizites Festlegen der **Verbindung** Eigenschaften **Anwendungseinstellungen** Eigenschaft **"false"** das Kennwort der DBML-Datei hinzugefügt wird.

## <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge mit den vertraulichen Informationen in den Anwendungseigenschaften des Projekts

- Klicken Sie auf **Ja**.

   Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert. Die Verbindungszeichenfolge enthält die vertraulichen Informationen als Klartext. Die vertraulichen Informationen sind nicht in der DBML-Datei enthalten.

## <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge ohne die vertraulichen Informationen in den Anwendungseigenschaften des Projekts

- Klicken Sie auf **keine**.

   Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert, jedoch ohne das Kennwort.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)