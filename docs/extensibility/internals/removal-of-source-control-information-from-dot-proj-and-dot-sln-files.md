---
title: Entfernen von Quellcodeverwaltungsinformationen aus .proj- und .sln-Dateien
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705586"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Entfernen von Informationen der Quellcodeverwaltung aus PROJ- und SLN-Dateien
In Version 1.2 der Quellcodeverwaltungs-Plug-in-API werden die SCC-Informationen in einem MSSCCPRJ gespeichert. SCC-Datei. Der Vorteil des MSSCCPRJ. SCC-Datei ist, dass die SCC-Informationen nicht von der Quelle gesteuert werden, wie es in .proj und .sln Dateien ist.

## <a name="version-12-changes"></a>Version 1.2 Änderungen
 In Quellcodeverwaltungs-Plug-Ins, die auf der Quellcodeverwaltungs-Plug-In-API Version 1.1 basieren, werden Informationen zur Quellcodeverwaltung in den Projektdateien (.proj) und Lösungsdateien (.sln) gespeichert. Der Speicherort der Quellcodeverwaltungsinformationen wird durch den AuxPath und der spezifische Speicherort in der Datenbank von ProjName angegeben. Dieses Verhalten kann nach Verzweigungs-, Gabel- oder Kopiervorgängen zu Problemen führen, da ProjName nach einem dieser Vorgänge in der Regel ungültig ist.

 In der Quellcodeverwaltungs-Plug-In-API-Version 1.1 verwendete die IDE die Dateien "SAK", um zu erkennen, ob ein Plug-In den MSSCCPRJ unterstützt. SCC-Methode zum Speichern von Quellcodeverwaltungsinformationen. Die Quellcodeverwaltungs-Plug-in-API-Version 1.2 bietet eine neue Funktion zum Erkennen der Unterstützung für MSSCCPRJ. SCC-Datei ohne Verwendung einer Datei mit dem Namen .SAK. Weitere Informationen finden Sie [unter Eliminierung von DATEIEN](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Weitere Informationen
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
