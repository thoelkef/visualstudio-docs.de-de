---
title: "Source Control-Plug-ins | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Verweis"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Source Control-Plug-ins
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Referenzabschnitt Source Control\-Plug\-in SDK enthält die vollständige Interface Specification, die Quellcode\-Verwaltungssysteme Integration ermöglicht [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Gibt die Syntax und Semantik der verschiedenen Funktionen und Daten, die das Quellcodeverwaltungs\-Plug\-in als Schnittstelle zu implementieren, muss der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\).  
  
## In diesem Abschnitt  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)  
 Führt Funktionen auf, die von dem Datenquellen\-Steuerelement\-Plug\-in implementiert werden müssen, um die Datenquellen\-Steuerelement\-Plug\-in\-API entsprechen.  
  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Beschreibt Funktionen, die das Quellcodeverwaltungs\-Plug\-in verwendet wird, um Informationen zur IDE zurück übergeben wird, während bestimmte Befehle ausgeführt werden.  
  
 [Enumeratoren](../extensibility/enumerators.md)  
 Der Enumerator\-Datentypen in der Quelle Steuerelement\-Plug\-in\-API, die das Quellcodeverwaltungs\-Plug\-in wissen muss, aufgeführt.  
  
 [Capability Flags](../extensibility/capability-flags.md)  
 Beschreibt die `SCC_CAP_xxx` Flags, die Funktionen des Providers angegeben werden.  
  
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)  
 Listet die Flags, die im Kontext von bestimmten Befehlen nützlich sind.  
  
 [Fehlercodes](../extensibility/error-codes.md)  
 Listet allgemeine Fehler Rückgabewerte von Funktionen als `SCCTRN`.  
  
 [Zeichenfolgen, die als Schlüssel für ein Quellcodeverwaltungs\-Plug\-in zu suchen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Beschreibt die Schlüssel für den Zugriff auf die Registrierung, um das Quellcodeverwaltungs\-Plug\-in finden.  
  
 [MSSCCPRJ. SCC\-Datei](../extensibility/mssccprj-scc-file.md)  
 Beschreibt eine clientseitige Datei, für die IDE nicht transparent, aber enthält, wird von das Quellcodeverwaltungs\-Plug\-in verwendet, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen.  
  
 [Bewährte Methoden für die Implementierung eines Datenquellen\-Steuerelements\-Plug\-in](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Stellt eine Auflistung der wichtigen technischen Erinnerungen, daran zu denken, während Sie die Datenquellen\-Steuerelement\-Plug\-in\-API implementieren.  
  
 [Einschränkungen der Zeichenfolge](../extensibility/restrictions-on-string-lengths.md)  
 Beschreibt Einschränkungen in der Source Control\-Plug\-in\-API auf die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.  
  
 [Glossar](../extensibility/source-control-plug-in-glossary.md)  
 Bietet hilfreiche Begriffe und ihrer Definitionen für die Source Control\-Plug\-in SDK\-Dokumentation lesen.  
  
 [Gewusst wie: Deaktivieren der Kompatibilität von Warnungen für Source Control\-Plug\-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Beschreibt das Deaktivieren von Warnungen.  
  
## Verwandte Abschnitte  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/de-de/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Enthält ein Beispiel der Quellcodeverwaltungsfunktionen\-Plug\-in.  
  
 [Test\-Handbuch für Source Control\-Plug\-ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Beschreibt, wie Tests im Zusammenhang mit der ein Quellcodeverwaltungs\-Plug\-in.  
  
 [Erstellen ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Beschreibt, wie Sie ein Quellcodeverwaltungs\-Plug\-in erstellen, das die Quellcodeverwaltungsfunktionen bereitstellt, während der Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Source Control\-Benutzeroberfläche \(UI\).  
  
 [Visual Studio SDK\-Referenz](../extensibility/visual-studio-sdk-reference.md)  
 Stellt eine Liste von Themen mit Referenzinformationen.