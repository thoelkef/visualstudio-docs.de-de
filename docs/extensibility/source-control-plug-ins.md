---
title: Source-Control-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b20d710b6a2ec51567fdffeeffeecde54c0f524
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983689"
---
# <a name="source-control-plug-ins"></a>Quellcodeverwaltungs-Plug-Ins
Der Referenzabschnitt Source Control-Plug-in SDK enthält die vollständige Benutzeroberfläche-Spezifikation, mit dem Quellcodeverwaltungs-Systeme integriert werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Es gibt an, die Syntax und Semantik der verschiedenen Funktionen und Daten, die das Quellcodeverwaltungs-Plug-in implementieren muss, um die Kommunikation mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)  
 Führt Funktionen auf, die durch das Quellcodeverwaltungs-Plug-in implementiert werden müssen, um die Datenquellen-Plug-in-API entsprechen.  
  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Beschreibt Funktionen, die das Quellcodeverwaltungs-Plug-in verwendet wird, um zurück zur IDE Informationen übergeben, während bestimmte Befehle ausgeführt werden.  
  
 [Enumeratoren](../extensibility/enumerators.md)  
 Listet die Datentypen der Enumerator in der Quelle Steuerelement-Plug-in-API, die das Quellcodeverwaltungs-Plug-in zu kennen müssen.  
  
 [Funktionsflags](../extensibility/capability-flags.md)  
 Beschreibt die `SCC_CAP_xxx` Flags, die Funktionen des Providers angegeben werden.  
  
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)  
 Listet die Flags, die im Kontext der bestimmten Befehle nützlich sind.  
  
 [Fehlercodes](../extensibility/error-codes.md)  
 Listet häufige Fehler Rückgabewerte von Funktionen als `SCCTRN`.  
  
 [Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Beschreibt die Schlüssel für den Zugriff auf die Registrierung, um das Quellcodeverwaltungs-Plug-in finden.  
  
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)  
 Beschreibt eine clientseitige Datei mit den Informationen, die für die IDE nicht transparent, aber wird, durch das Quellcodeverwaltungs-Plug-in, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen.  
  
 [Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-ins](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Stellt eine Auflistung der wichtigen technischen Erinnerungen zu merken, während Sie die Datenquellen-Plug-in-API implementieren.  
  
 [Einschränkungen für die Längen von Zeichenfolgen](../extensibility/restrictions-on-string-lengths.md)  
 Beschreibt die Einschränkungen in der Quelle-Plug-in-API für die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.  
  
 [Glossar](../extensibility/source-control-plug-in-glossary.md)  
 Bietet nützliche Begriffe und ihre Definitionen für die Source-Control-Plug-in SDK-Dokumentation lesen.  
  
 [Vorgehensweise: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Beschreibt, wie ein, um Warnungen zu deaktivieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Beispiel für Datenquellen-Steuerelement-Plug-in](https://www.microsoft.com/download/details.aspx?id=55984)  
 Enthält ein Beispiel der Quellcodeverwaltungsfunktionen-Plug-in.  
  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Beschreibt, wie Tests im Zusammenhang mit der ein Quellcodeverwaltungs-Plug-in.  
  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, die Quellcodeverwaltungsfunktionen bereitstellt, während der Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Source Control-Benutzeroberfläche (UI).  
  
 [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)  
 Zeigt eine Liste von Themen der Referenz.