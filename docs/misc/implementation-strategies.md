---
title: "Implementierungsstrategien | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, Implementierungsstrategien"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Implementierungsstrategien
Sie können Visual Studio mit Automatisierungs\-Add\-Ins, VSPackages, MEF\-Komponenten \(Managed Extensibility Framework\) oder mit einer Kombination der drei Optionen erweitern. Add\-Ins sind im Allgemeinen einfacher zu entwickeln, aber weniger leistungsfähig als VSPackages oder MEF\-Komponenten. Add\-Ins können Erweiterungsschnittstellen aufrufen, während VSPackages und MEF\-Komponenten auf das Visual Studio\-Automatisierungsmodell zugreifen können. Sie können verschiedene unterschiedliche Ansätze zum Erstellen einer effektiven Lösung kombinieren.  
  
 VSPackages können in nicht verwaltetem oder verwaltetem Code geschrieben werden. Es wird empfohlen, dass Sie neue VSPackages mithilfe des Managed Package Framework \(MPF\) in verwaltetem Code schreiben. Fast alles, das in nicht verwaltetem Code geschrieben werden kann, kann einfacher und sicherer in verwaltetem Code implementiert werden. In nicht verwaltetem Code geschriebene Legacyanwendungen können jedoch weiterhin in Visual Studio ausgeführt werden.  
  
 Einfache Erweiterungen können Toolfenster hinzufügen oder Informationen an UI\-Elemente von Visual Studio senden, z. B. an die Statusleiste oder das Ausgabefenster. Komplexere Anwendungen können als Visual Studio\-Hierarchien geschrieben werden, z. B. der Server\-Explorer. Wenn Sie ein Projekt, einen Editor oder einen Designer implementieren, erhalten Sie noch mehr Leistung.[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wurden z. B. selbst als Sprachdienste implementiert.  
  
## Verwandte Abschnitte  
 [Visual Studio SDK und Automatisierung](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Erläutert die Verwendung von Automatisierung, VSPackages oder einer Kombination aus beidem zum Erstellen von Visual Studio\-Erweiterbarkeitsanwendungen.  
  
 [Visual Studio SDK und verwalteter Code](../misc/visual-studio-sdk-and-managed-code.md)  
 Vergleicht die verschiedenen Möglichkeiten, wie Sie ein VSPackage in verwaltetem Code schreiben können.  
  
 [Visual Studio\-IDE\-Konzepte](../misc/visual-studio-ide-concepts.md)  
 Erläutert die Grundlagen von VSPackages sowie die Verwendung eines Diensts.  
  
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert allgemeine Anwendungselemente der Benutzeroberfläche in Visual Studio, z. B. Status\- und Ausgabefenster.  
  
 [Hierarchien in Visual Studio](../extensibility/internals/hierarchies-in-visual-studio.md)  
 Bietet eine Übersicht über Visual Studio\-Hierarchien, die in der integrierten Entwicklungsumgebung \(IDE\) als Strukturen von Knoten angezeigt werden.  
  
 [Projekte](../extensibility/internals/projects.md)  
 Bietet eine Übersicht über Projekt\- und Projektmappenklassen.  
  
 [\-Editor, und Language Service Extensions](../extensibility/editor-and-language-service-extensions.md)  
 Veranschaulicht die Erweiterung von Code\- und Text\-Editor sowie die Erstellung benutzerdefinierter Editoren und Designer.  
  
 [Ältere Sprache Service\-Erweiterbarkeit](../extensibility/internals/legacy-language-service-extensibility.md)  
 Veranschaulicht die Erstellung von Sprachdiensten.  
  
 [Visual Studio SDK\-Referenz](../extensibility/visual-studio-sdk-reference.md)  
 Die Referenzdokumentation für VSSDK.  
  
## Siehe auch  
 [Starten Visual Studio\-Erweiterungen entwickeln](../extensibility/starting-to-develop-visual-studio-extensions.md)