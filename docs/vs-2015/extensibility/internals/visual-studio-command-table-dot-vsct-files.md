---
title: Visual Studio-Befehlstabelle (. VSCT)-Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0692f0b32544edf7d5d7cec4b0ab4592c4219b3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521713"
---
# <a name="visual-studio-command-table-vsct-files"></a>VSCT-Dateien (Visual Studio Command Table)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual Studio Command Table (. VSCT) Dateien](https://docs.microsoft.com/visualstudio/extensibility/internals/visual-studio-command-table-dot-vsct-files).  
  
Konfiguration eine Befehlsdatei-Tabelle ist eine Textdatei, die den Satz von Befehlen zu beschreiben, die VSPackages enthält. Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Befehl Tabelle (VSCT)-Compiler kompiliert XML-basierten Konfiguration (VSCT-Dateien) in binäre Befehl Tabelle Ausgabedateien (CTO). Die resultierende CTO-Dateien sind identisch mit denen, die mit dem Befehl-Tabelle (CTC)-Compiler zum Kompilieren der CTC-Konfigurationsdateien erstellt werden. XML-basierte VSCT-Dateien hat jedoch einige Vorteile, z. B. eine XML-Editor und IntelliSense für XML.  
  
 Weitere Informationen zu der Syntax und Semantik der VSCT-Dateien finden Sie unter [Entwerfen von XML-Command Table (. VSCT)-Dateien](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwerfen von Dateien für XML-Befehlstabellen (VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Beschreibt das Entwerfen der VSCT-Dateien.  
  
 [Gewusst wie: Erstellen einer VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Vergleicht die Methoden zum Erstellen einer VSCT-Datei an. Beschreibt den Prozess zum manuellen Erstellen eine neue VSCT-Datei.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)  
 Enthält Details zu jedem Abschnitt des Befehls Tabelle XML-Datei.  
  
 [Konfiguration der Befehl (. CTC)-Dateien](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Bietet eine Übersicht über das veraltete CTC-Dateiformat.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Beschreibt die Formatspezifikation der Befehl-Tabelle.  
  
 [Ressourcen in VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Beschreibt die Verwendung von verwalteten und nicht verwalteten Ressourcen in verwaltete VSPackages.  
  
 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.

