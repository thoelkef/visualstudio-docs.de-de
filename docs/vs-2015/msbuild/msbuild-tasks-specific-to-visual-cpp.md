---
title: Spezifische MSBuild-Aufgaben für Visual C++ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686909"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Spezifische MSBuild-Aufgaben für Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Wenn Visual C++ installiert wird, sind die folgenden Aufgaben zusätzlich zu den Aufgaben verfügbar, die mit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] installiert sind. Weitere Informationen finden Sie unter [Übersicht über MSBuild (Visual C++)](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Zusätzlich zu den Parametern für jede Aufgabe hat jede Aufgabe auch die folgenden Parameter.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionaler `String`-Parameter.<br /><br /> Ein `Boolean`-Ausdruck, den die [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Engine verwendet, um zu bestimmen, ob diese Aufgabe ausgeführt wird. Informationen zu den Bedingungen, die von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] unterstützt werden, finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionaler Parameter. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[BSCMAKE-Aufgabe](../msbuild/bscmake-task.md)|Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (bscmake.exe).|  
|[CL-Aufgabe](../msbuild/cl-task.md)|Umschließt das Visual C++-Compilertool (cl.exe).|  
|[Cppclean-Aufgabe](../msbuild/cppclean-task.md)|Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C++-Projekt erstellt wird.|  
|[LIB-Aufgabe](../msbuild/lib-task.md)|Umschließt das 32-Bit-Tool von Microsoft zur Bibliotheksverwaltung (lib.exe).|  
|[Link-Aufgabe](../msbuild/link-task.md)|Umschließt das Visual C++-Linkertool (link.exe).|  
|[Mittel l-Aufgabe](../msbuild/midl-task.md)|Umschließt das MIDL-Compilertool (Microsoft Interface Definition Language) (midl.exe).|  
|[MT-Aufgabe](../msbuild/mt-task.md)|Umschließt das Microsoft Manifesttool (mt.exe).|  
|[RC-Aufgabe](../msbuild/rc-task.md)|Umschließt das Microsoft Windows-Ressourcencompilertool (rc.exe).|  
|[-Aufgabe](../msbuild/setenv-task.md)|Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.|  
|[Vcmessage-Aufgabe](../msbuild/vcmessage-task.md)|Protokolliert Warn- und Fehlermeldungen während eines Builds.|  
|[XDCMake-Aufgabe](../msbuild/xdcmake-task.md)|Umschließt das XML-Dokumentationstool (xdcmake.exe), das die XML-Dokument-Kommentardateien (.xdc) in einer XML-Datei zusammengeführt.|  
|[XSD-Aufgabe](../msbuild/xsd-task.md)|Umschließt das XML-Schemadefinitionstool (xsd.exe), das Schema- oder Klassendateien aus einer Quelle generiert.|  
|[MSBuild-Referenz](../msbuild/msbuild-reference.md)|Beschreibt die Elemente des MSBuild-Systems.|  
|[Aufgaben](../msbuild/msbuild-tasks.md)|Beschreibt die Aufgaben, die Einheiten von Code darstellen, die kombiniert werden können, um einen Build zu erstellen.|  
|[Schreiben von Aufgaben](../msbuild/task-writing.md)|Beschreibt das Erstellen einer Aufgabe.|
