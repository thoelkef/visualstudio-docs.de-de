---
title: Visual Studio-Befehlstabelle (. VSCT)-Dateien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio-Befehlstabelle (. VSCT)-Dateien
Eine Befehl Tabelle-Konfigurationsdatei ist eine Textdatei, die den Satz von Befehlen zu beschreiben, die eine VSPackage enthält. Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehl Tabelle (VSCT)-Compiler kompiliert XML-basierte Konfigurationsdateien (VSCT-Dateien) in binäre Befehl Tabelle Ausgabedateien (CTO). Die resultierenden CTO-Dateien sind identisch mit denen, die mit dem Befehl-Tabelle (CTC)-Compiler zum Kompilieren der CTC-Konfigurationsdateien erstellt werden. XML-basierte VSCT-Dateien hat jedoch einige Vorteile, z. B. einem XML-Editor, und IntelliSense für XML.  
  
 Um weitere Informationen über die Syntax und Semantik der VSCT-Dateien finden Sie unter [XML-Befehl-Tabelle entwerfen (. VSCT)-Dateien](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwerfen von Dateien für XML-Befehlstabellen (VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Beschreibt die VSCT-Dateien zu entwerfen.  
  
 [Gewusst wie: Erstellen einer VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Vergleicht die Methoden zum Erstellen einer VSCT-Datei an. Beschreibt den Prozess zum manuellen Erstellen eine neue VSCT-Datei.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)  
 Enthält Details zu jeder Abschnitt der Befehl Tabelle XML-Konfigurationsdatei.  
  
 [Konfiguration der Befehl (. CTC)-Dateien](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Bietet eine Übersicht über das veraltete CTC-Dateiformat.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Beschreibt den Befehl Tabelle Formatangabe.  
  
 [Ressourcen in VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Beschreibt, wie verwaltete und nicht verwaltete Ressourcen in verwaltete VSPackages.  
  
 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.