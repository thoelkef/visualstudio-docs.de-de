---
title: BscMake-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff0c95c37e24f8c51453a849159073baff8dca0d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593420"
---
# <a name="bscmake-task"></a>BscMake-Aufgabe
> [!IMPORTANT]
> BscMake wird nicht mehr von der Visual Studio-IDE verwendet werden. Seit Visual Studio 2008 werden Browseinformationen automatisch in einer *SDF*-Datei im *Projektmappenordner* gespeichert.

 Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (*bscmake.exe*).  Das Tool *bscmake.exe* erstellt eine Browseinformationsdatei ( *.bsc*) von Quellbrowserdateien ( *.sbr*), die während der Kompilierung erstellt werden. Verwenden Sie den **Objektkatalog**, um eine *BSC*-Datei anzuzeigen. Weitere Informationen finden Sie unter [BSCMAKE-Referenz](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der **BscMake**-Aufgabe beschrieben. Die meisten Aufgabenparameter entsprechen einer Befehlszeilenoption.

|Parameter|Beschreibung|
|---------------|-----------------|
|**AdditionalOptions**|Optionaler **String**-Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben. Zum Beispiel „/\<Option1> /\<Option2> /\<Option#>“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **BscMake**-Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter den Optionen in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Optionaler **String**-Parameter.<br /><br /> Gibt einen Dateinamen an, der den Standardausgabedateinamen überschreibt.<br /><br /> Weitere Informationen finden Sie unter der **/o**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird ein nicht inkrementelles Erstellen erzwungen. Ein vollständiges nicht inkrementelles Erstellen tritt unabhängig davon auf, ob eine *BSC*-Datei vorhanden ist, und verhindert, dass *SBR*-Dateien abgeschnitten werden.<br /><br /> Weitere Informationen finden Sie unter der **/n**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|
|**Sources**|Optionaler **ITaskItem[]** -Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|
|**SuppressStartupBanner**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der **/NOLOGO**-Option in [BSCMAKE-Optionen](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.|

## <a name="see-also"></a>Siehe auch
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
