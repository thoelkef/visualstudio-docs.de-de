---
title: MSSCCPRJ. SCC-Datei | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702470"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. SCC-Datei
Wenn Sie eine Visual Studio-Projektmappe oder ein Visual Studio-Projekt mithilfe der IDE unter Quellcodeverwaltung platzieren, erhält die IDE zwei wichtige Informationen. Die Informationen stammen aus dem Quellcodeverwaltungs-Plug-In in Form von Zeichenfolgen. Diese Zeichenfolgen, "AuxPath" und "ProjName", sind für die IDE undurchsichtig, werden jedoch vom Plug-In verwendet, um die Projektmappe oder das Projekt in der Versionskontrolle zu finden. Die IDE ruft diese Zeichenfolgen in der Regel zum ersten Mal ab, indem sie [SccGetProjPath](../extensibility/sccgetprojpath-function.md)aufruft, und speichert sie dann in der Projektmappe oder Projektdatei für zukünftige Aufrufe des [SccOpenProject](../extensibility/sccopenproject-function.md). Wenn die Zeichenfolgen "AuxPath" und "ProjName" in die Projektmappen- und Projektdateien eingebettet sind, werden sie nicht automatisch aktualisiert, wenn ein Benutzer Projektmappen- oder Projektdateien, die sich in der Versionskontrolle befinden, verzweigt, verzweigt oder kopiert. Um sicherzustellen, dass die Projektmappen- und Projektdateien auf ihren richtigen Speicherort in der Versionskontrolle verweisen, müssen Benutzer die Zeichenfolgen manuell aktualisieren. Da die Zeichenfolgen undurchsichtig sein sollen, ist möglicherweise nicht immer klar, wie sie aktualisiert werden sollen.

 Das Quellcodeverwaltungs-Plug-In kann dieses Problem vermeiden, indem es die Zeichenfolgen "AuxPath" und "ProjName" in einer speziellen Datei namens *MSSCCPRJ.SCC-Datei* speichert. Es handelt sich um eine lokale, clientseitige Datei, die im Besitz des Plug-Ins ist und vom Plug-In verwaltet wird. Diese Datei wird nie unter Quellcodeverwaltung gestellt, sondern wird vom Plug-In für jedes Verzeichnis generiert, das Dateien unter Quellcodeverwaltung enthält. Um zu bestimmen, welche Dateien Visual Studio-Projektmappen- und Projektdateien sind, kann ein Quellcodeverwaltungs-Plug-In die Dateierweiterungen mit einer Standard- oder vom Benutzer bereitgestellten Liste vergleichen. Sobald die IDE erkennt, dass ein Plug-In die *MSSCCPRJ.SCC-Datei* unterstützt, wird die Zeichenfolgen "AuxPath" und "ProjName" nicht mehr in Lösungs- und Projektdateien eingebettet, und sie liest diese Zeichenfolgen stattdessen aus der *MSSCCPRJ.SCC-Datei.*

 Ein Quellcodeverwaltungs-Plug-In, das die *MSSCCPRJ.SCC-Datei* unterstützt, muss die folgenden Richtlinien befolgen:

- Es kann nur eine *MSSCCPRJ.SCC-Datei* pro Verzeichnis vorhanden sein.

- Eine *MSSCCPRJ.SCC-Datei* kann den "AuxPath" und "ProjName" für mehrere Dateien enthalten, die sich in einem bestimmten Verzeichnis unter Quellcodeverwaltung befinden.

- Die Zeichenfolge "AuxPath" darf keine Anführungszeichen enthalten. Es ist erlaubt, Anführungszeichen um sie herum als Trennzeichen zu haben (z. B. kann ein Paar von doppelten Anführungszeichen verwendet werden, um eine leere Zeichenfolge anzuzeigen). Die IDE entfernt alle Anführungszeichen aus der Zeichenfolge "AuxPath", wenn sie aus der *MSSCCPRJ.SCC-Datei* gelesen wird.

- Die Zeichenfolge "ProjName" im *MSSCCPRJ. Die SCC-Datei* muss genau `SccGetProjPath` mit der Zeichenfolge übereinstimmen, die von der Funktion zurückgegeben wird. Wenn die von der Funktion zurückgegebene Zeichenfolge Anführungszeichen enthält, muss die Zeichenfolge in der *MSSCCPRJ.SCC-Datei* Anführungszeichen um sie herum haben und umgekehrt.

- Eine *MSSCCPRJ.SCC-Datei* wird erstellt oder aktualisiert, wenn eine Datei unter Quellcodeverwaltung gestellt wird.

- Wenn eine *MSSCCPRJ.SCC-Datei* gelöscht wird, sollte ein Anbieter sie neu generieren, wenn er das nächste Mal einen Quellcodeverwaltungsvorgang für dieses Verzeichnis ausführt.

- Eine *MSSCCPRJ.SCC-Datei* muss strikt dem definierten Format folgen.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Eine Abbildung des MSSCCPRJ. SCC-Dateiformat
 Im Folgenden finden Sie ein Beispiel für das *MSSCCPRJ.SCC-Dateiformat* (die Zeilennummern werden nur als Leitfaden bereitgestellt und sollten nicht im Dateitext enthalten sein):

- [Zeile 1]`SCC = This is a Source Code Control file`

- [Zeile 2]

- [Zeile 3]`[TestApp.sln]`

- [Zeile 4]`SCC_Aux_Path = "\\server\vss\"`

- [Zeile 5]`SCC_Project_Name = "$/TestApp"`

- [Zeile 6]

- [Zeile 7]`[TestApp.csproj]`

- [Zeile 8]`SCC_Aux_Path = "\\server\vss\"`

- [Zeile 9]`SCC_Project_Name = "$/TestApp"`

 Die erste Zeile gibt den Zweck der Datei an und dient als Signatur für alle Dateien dieses Typs. Diese Zeile sollte in allen *MSSCCPRJ.SCC-Dateien* genau so erscheinen:

 `SCC = This is a Source Code Control file`

 Im folgenden Abschnitt werden die Einstellungen für jede Datei beschrieben, die durch den Dateinamen in eckigen Klammern gekennzeichnet sind. Dieser Abschnitt wird für jede nachverfolgte Datei wiederholt. Diese Zeile ist ein Beispiel für `[TestApp.csproj]`einen Dateinamen, nämlich . Die IDE erwartet die folgenden beiden Zeilen. Es definiert jedoch nicht den Stil der definierten Werte. Die Variablen `SCC_Aux_Path` `SCC_Project_Name`sind und .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Es gibt kein Endtrennzeichen für diesen Abschnitt. Der Name der Datei sowie alle Literale, die in der Datei angezeigt werden, werden in der Scc.h-Headerdatei definiert. Weitere Informationen finden Sie unter [Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendet werden.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendet werden](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
