---
title: "Spezifische MSBuild-Aufgaben für Visual C++ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: a3521e5a8f0bcf3d6d938187031b9a2de73b20d5
ms.lasthandoff: 04/05/2017

---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Spezifische MSBuild-Aufgaben für Visual C++
Aufgaben stellen den Code bereit, der während des Buildprozesses ausgeführt wird. Wenn Visual C++ installiert wird, sind die folgenden Aufgaben zusätzlich zu den Aufgaben verfügbar, die mit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] installiert sind. Weitere Informationen finden Sie unter [Übersicht über MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview).  
  
 Zusätzlich zu den Parametern für jede Aufgabe hat jede Aufgabe auch die folgenden Parameter.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionaler `String`-Parameter.<br /><br /> Ein `Boolean`-Ausdruck, den das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Modul verwendet, um zu bestimmen, ob diese Aufgabe ausgeführt wird. Informationen zu den Bedingungen, die von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt werden, finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Optionaler Parameter. Kann einen oder mehrere der folgenden Werte enthalten:<br /><br /> -   **WarnAndContinue** oder **true**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element [Ziel](../msbuild/target-element-msbuild.md) und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Warnungen behandelt.<br />-   **ErrorAndContinue**. Wenn eine Aufgabe fehlschlägt, werden nachfolgende Aufgabe im Element `Target` und im Build weiterhin ausgeführt, und alle Fehler von der Aufgabe werden als Fehler behandelt.<br />-   **ErrorAndStop** oder **false** (Standard). Wenn eine Aufgabe fehlschlägt, werden die übrigen Aufgaben im Element `Target` und im Build nicht ausgeführt, und das komplette Element `Target` sowie der Build wird als fehlgeschlagen betrachtet.<br /><br /> Versionen von .NET Framework vor 4.5 unterstützten nur die Werte `true` und `false`.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Ignorieren von Fehlern in Aufgaben](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[BscMake-Aufgabe](../msbuild/bscmake-task.md)|Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (bscmake.exe).|  
|[CL-Aufgabe](../msbuild/cl-task.md)|Umschließt das Visual C++-Compilertool (cl.exe).|  
|[CPPClean-Aufgabe](../msbuild/cppclean-task.md)|Löscht die temporären Dateien, die MSBuild erstellt, wenn ein Visual C++-Projekt erstellt wird.|  
|[LIB-Aufgabe](../msbuild/lib-task.md)|Umschließt das 32-Bit-Tool von Microsoft zur Bibliotheksverwaltung (lib.exe).|  
|[Link-Aufgabe](../msbuild/link-task.md)|Umschließt das Visual C++-Linkertool (link.exe).|  
|[MIDL-Aufgabe](../msbuild/midl-task.md)|Umschließt das MIDL-Compilertool (Microsoft Interface Definition Language) (midl.exe).|  
|[MT-Aufgabe](../msbuild/mt-task.md)|Umschließt das Microsoft Manifesttool (mt.exe).|  
|[RC-Aufgabe](../msbuild/rc-task.md)|Umschließt das Microsoft Windows-Ressourcencompilertool (rc.exe).|  
|[SetEnv Task](../msbuild/setenv-task.md)|Legt den Wert einer bestimmten Umgebungsvariable fest oder löscht ihn.|  
|[VCMessage-Aufgabe](../msbuild/vcmessage-task.md)|Protokolliert Warn- und Fehlermeldungen während eines Builds.|  
|[XDCMake-Aufgabe](../msbuild/xdcmake-task.md)|Umschließt das XML-Dokumentationstool (xdcmake.exe), das die XML-Dokument-Kommentardateien (.xdc) in einer XML-Datei zusammengeführt.|  
|[XSD-Aufgabe](../msbuild/xsd-task.md)|Umschließt das XML-Schemadefinitionstool (xsd.exe), das Schema- oder Klassendateien aus einer Quelle generiert.|  
|[MSBuild-Referenz](../msbuild/msbuild-reference.md)|Beschreibt die Elemente des MSBuild-Systems.|  
|[Tasks](../msbuild/msbuild-tasks.md) (MSBuild-Aufgaben)|Beschreibt die Aufgaben, die Einheiten von Code darstellen, die kombiniert werden können, um einen Build zu erstellen.|  
|[Schreiben von Aufgaben](../msbuild/task-writing.md)|Beschreibt das Erstellen einer Aufgabe.|
