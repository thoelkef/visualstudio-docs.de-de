---
title: Source Control-Plug-ins | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea5169b3d74a77bbb079dab5b310a3b7ebbbeff0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-plug-ins"></a>Datenquellen-Steuerelement-Plug-ins
Der Referenzabschnitt Source Control-Plug-in SDK enthält die vollständige Benutzeroberfläche-Spezifikation, mit dem Quellcode-Verwaltungssysteme mit integriert werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Gibt an, die Syntax und Semantik der verschiedenen Funktionen und Daten, die die Datenquellen-Steuerelements, das plug-in implementieren muss, für die Kommunikation mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)  
 Führt Funktionen auf, die von der quellcodeverwaltung-Plug-in implementiert werden müssen, damit Sie um mit der Source Control-Plug-in-API zu erfüllen.  
  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Beschreibt Funktionen, die das Quellsteuerelement-Plug-in verwendet wird, um Informationen an der IDE übergeben wird, während bestimmte Befehle ausgeführt werden.  
  
 [Enumeratoren](../extensibility/enumerators.md)  
 Listet die Enumerator-Datentypen in der Quelle Steuerelement-Plug-in-API, die die Datenquellen-Steuerelement-Plug-in zu kennen muss.  
  
 [Funktionsflags](../extensibility/capability-flags.md)  
 Beschreibt die `SCC_CAP_xxx` Flags, die Funktionen des Anbieters angegeben werden.  
  
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)  
 Listet die Flags, die im Kontext der bestimmten Befehlen nützlich sind.  
  
 [Fehlercodes](../extensibility/error-codes.md)  
 Listet häufige Fehler Rückgabewerte von Funktionen als `SCCTRN`.  
  
 [Als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendete Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Beschreibt die Schlüssel für den Zugriff auf die Registrierung, um die Datenquellen-Steuerelement-Plug-in ermitteln.  
  
 [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)  
 Beschreibt eine clientseitige Datei enthält Informationen, die für die IDE nicht transparent, aber, wird von der quellcodeverwaltung-Plug-in verwendet, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen.  
  
 [Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-ins](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Stellt eine Auflistung der wichtigen technischen Erinnerungen zu merken, während Sie die Datenquellen-Steuerelement-Plug-in-API implementieren.  
  
 [Einschränkungen für die Längen von Zeichenfolgen](../extensibility/restrictions-on-string-lengths.md)  
 Beschreibt die Einschränkungen in der Quelle Steuerelement-Plug-in-API auf die Länge der Zeichenfolgen, die in verschiedenen Funktionen verwendet.  
  
 [Glossar](../extensibility/source-control-plug-in-glossary.md)  
 Bietet hilfreiche Begriffe und ihre Definitionen für die Datenquellen-Steuerelement-Plug-in SDK-Dokumentation lesen.  
  
 [Gewusst wie: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Beschreibt, wie Warnungen deaktivieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Plug-in-Beispiel für die Datenquellen-Steuerelement](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Enthält ein Beispiel der Quellcodeverwaltungsfunktion-Plug-in.  
  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Beschreibt Testverfahren im Zusammenhang mit der ein Quellcodeverwaltungs-Plug-in.  
  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, das Quellcodeverwaltungsfunktion bereitstellt, während der Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Quelle Steuerelement-Benutzeroberfläche (UI).  
  
 [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md)  
 Zeigt eine Liste von Themen mit Referenzinformationen.