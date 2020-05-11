---
title: Bewährte Methoden zum Implementieren eines Quellcodeverwaltungs-Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740052"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-Ins
Die folgenden technischen Details können Ihnen helfen, ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Quellcodeverwaltungs-Plug-In in zuverlässig zu implementieren.

## <a name="memory-management-issues"></a>Probleme mit der Speicherverwaltung
 In den meisten Fällen gibt die integrierte Entwicklungsumgebung (IDE), die der Aufrufer ist, Speicher frei und weist sie zu. Das Quellcodeverwaltungs-Plug-In gibt Zeichenfolgen und andere Elemente in vom Aufrufer zugewiesenen Puffern zurück. Ausnahmen werden in Beschreibungen bestimmter Funktionen erwähnt, in denen sie auftreten.

## <a name="arrays-of-file-names"></a>Arrays von Dateinamen
 Wenn ein Array von Dateien übergeben wird, wird es nicht als zusammenhängendes Array von Dateinamen übergeben. Es wird als Array von Zeigern an Dateinamen übergeben. Im [SccGet](../extensibility/sccget-function.md)werden z. B. die `lpFileNames` Dateinamen `lpFileNames` vom Parameter übergeben, `char **`wobei es sich tatsächlich um einen Zeiger auf eine handelt. `lpFileNames`[0] ist ein Zeiger auf `lpFileNames`den Vornamen, [1] ist ein Zeiger auf den zweiten Namen usw.

## <a name="large-model"></a>Großes Modell
 Alle Zeiger sind 32 Bit, auch auf 16-Bit-Betriebssystemen.

## <a name="fully-qualified-paths"></a>Vollqualifizierte Pfade
 Wenn Dateinamen oder Verzeichnisse als Argumente angegeben werden, müssen sie vollqualifizierte Pfade oder UNC-Pfade ohne die endende umgekehrte Schrägstriche sein. Es liegt in der Verantwortung des Quellcodeverwaltungs-Plug-Ins, diese in relative Pfade zu übersetzen, wenn dies eine Anforderung des zugrunde liegenden Quellcodeverwaltungssystems ist.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Angeben eines vollqualifizierten Pfads für die registrierte DLL
 Die IDE lädt keine DLLs mehr von relativen Pfaden (z. B. *.'NewProvider.dll ').* Es muss ein vollständiger Pfad der DLL angegeben werden (z. B. *C:-Providers-NewProvider.dll*). Diese Anforderung erhöht die Sicherheit der IDE, indem das Laden nicht autorisierter oder imitierter Quellcodeverwaltungs-DLLs verhindert wird.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Überprüfen Sie, ob ein vorhandenes VSSCI-Plug-In vorhanden ist, wenn Sie Ihr Quellcodeverwaltungs-Plug-In installieren
 Ein Benutzer, der das Quellcodeverwaltungs-Plug-In installieren möchte, hat möglicherweise bereits ein vorhandenes Quellcodeverwaltungs-Plug-In auf dem Computer installiert. Das Installationsprogramm (Setup) für das von Ihnen erstellte Plug-In sollte bestimmen, ob Werte für die entsprechenden Registrierungsschlüssel vorhanden sind. Wenn diese Schlüssel bereits festgelegt sind, sollte das Installationsprogramm den Benutzer fragen, ob Sie Ihr Plug-In als Standard-Quellcodeverwaltungs-Plug-In registrieren und das bereits installierte ersetzen sollten.

## <a name="error-result-codes-and-reporting"></a>Fehlerergebniscodes und Berichterstellung
 Der `SCC_OK` Rückgabecode für eine Quellcodeverwaltungsfunktion gibt an, dass der Vorgang für alle Dateien erfolgreich war. Wenn der Vorgang fehlschlägt, wird erwartet, dass der zuletzt gefundene Fehlercode zurückgegeben wird.

 Die Regel für die Meldung lautet, dass, wenn ein Fehler in der IDE auftritt, die IDE für die Meldung verantwortlich ist. Wenn im Quellcodeverwaltungssystem ein Fehler auftritt, ist das Quellcodeverwaltungs-Plug-In für die Meldung verantwortlich. Beispielsweise werden **derzeit keine Dateien** von der IDE gemeldet, während diese Datei bereits **ausgecheckt** vom Plug-In gemeldet wird.

## <a name="the-context-structure"></a>Die Kontextstruktur
 Während des Aufrufs der [SccInitialize](../extensibility/sccinitialize-function.md)übergibt der Aufrufer den `ppvContext` Parameter, bei dem es sich um ein nicht initialisiertes Handle handelt, an eine leere. Das Quellcodeverwaltungs-Plug-In kann diesen Parameter ignorieren oder eine Struktur jeglicher Art zuweisen und einen Zeiger auf diese Struktur in den übergebenen Zeiger setzen. Die IDE versteht diese Struktur nicht, aber sie gibt einen Zeiger auf diese Struktur an jeden anderen Aufruf im Plug-In weiter. Dadurch werden dem Plug-In wertvolle Kontextcacheinformationen zur Verfügung, mit denen es globale Statusinformationen verwaltet, die über Funktionsaufrufe hinweg beibehalten werden, ohne globale Variablen zu verwenden. Das Plug-In ist für die Freigabe der Struktur bei einem Aufruf an die [SccUninitialize](../extensibility/sccuninitialize-function.md)verantwortlich.

 Wenn das Plug-In `SCC_CAP_REENTRANT` das Bit in [Der SccInitialize](../extensibility/sccinitialize-function.md) (speziell im `lpSccCaps` Parameter) festlegt, werden mehrere Kontextstrukturen verwendet, um alle geöffneten Projekte nachzuverfolgen.

## <a name="bitflags-and-other-command-options"></a>Bitflags und andere Befehlsoptionen
 Für jeden Befehl, z. B. [SccGet](../extensibility/sccget-function.md), kann die IDE viele Optionen angeben, die das Verhalten des Befehls ändern.

 Die API unterstützt die Einstellung bestimmter Optionen `fOptions` durch die IDE über den Parameter. Diese Optionen werden in [Bitflags beschrieben,](../extensibility/bitflags-used-by-specific-commands.md) die von bestimmten Befehlen zusammen mit den befehlsgebenden Befehlen verwendet werden. Im Allgemeinen sind dies Optionen, für die der Benutzer nicht aufgefordert wird.

 Die meisten benutzerkonfigurierbaren Einstellungsoptionen sind auf diese Weise nicht definiert, da sie zwischen den Quellcodeverwaltungs-Plug-Ins sehr unterschiedlich sind. Daher ist der empfohlene **Advanced** Mechanismus eine Advanced-Taste. Im Dialogfeld **Abrufen** zeigt die IDE beispielsweise nur Informationen an, die sie versteht, aber sie zeigt auch eine **Schaltfläche "Erweitert"** an, wenn das Plug-In Optionen für diesen Befehl enthält. Wenn der Benutzer auf die Schaltfläche **Erweitert** klickt, ruft die IDE die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) auf, damit das Quellcodeverwaltungs-Plug-In den Benutzer zur Eingabe von Informationen wie Bitflags oder einem Datum/Uhrzeit auffordert. Das Plug-In gibt diese Informationen in einer `SccGet` Struktur zurück, die während des Befehls zurückgegeben wird.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)
