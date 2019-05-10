---
title: XSD-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d306ec78087ed53ceca44b15f2e184397217650
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584022"
---
# <a name="xdcmake-task"></a>XDCMake-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Umschließt das XML-Dokumentationstool (xdcmake.exe), das die XML-Dokument-Kommentardateien (.xdc) in einer XML-Datei zusammengeführt.  
  
 Es wird eine XDC-Datei erstellt, wenn Sie Dokumentationskommentare in Ihren Visual C++-Quellcode eingeben und mithilfe der Compileroption [/doc](http://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) kompilieren. Weitere Informationen finden Sie unter [XDCMake-Verweis](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Eigenschaftenseiten für das Tool XML-Dokument-Generator](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) und unter der Befehlszeilenhilfe-Option (**/?**) für xdcmake.exe.  
  
## <a name="remarks"></a>Anmerkungen  
 Standardmäßig unterstützt das xdcmake.exe-Tool einige Befehlszeilenoptionen. Zusätzliche Optionen werden bei der Angabe der **/old**-Befehlszeilenoption unterstützt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **XDCMake**-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Optionaler **String[]**-Parameter.<br /><br /> Gibt eine oder mehrere weitere XDC-Dateien zum Zusammenführen an.<br /><br /> Weitere Informationen finden Sie unter der Beschreibung **Zusätzliche Dokumentdateien** unter [Eigenschaftenseiten für das XML-Dokument-Generator-Tool](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Sehen Sie sich auch die **/old**- und **/FS**-Befehlszeilenoptionen für xdcmake.exe an.|  
|**AdditionalOptions**|Optionaler **String**-Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: „*/option1 /option2 /option#*“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XDCMake**-Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter [XDCMake-Verweis](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Eigenschaftenseiten für das Tool XML-Dokument-Generator](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) und unter der Befehlszeilenhilfe (**/?**) für xdcmake.exe.|  
|**DocumentLibraryDependencies**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn `true` und das aktuelle Projekt über eine Abhängigkeit in einem statischen Bibliotheksprojekt (.lib) in der Projektmappe verfügen, werden die XDC-Dateien für das Bibliotheksprojekt in der XML-Dateiausgabe für das aktuelle Projekt eingefügt.<br /><br /> Weitere Informationen finden Sie in der Beschreibung **Dokumentbibliothekabhängigkeiten** unter [Eigenschaftenseiten für das Tool XML-Dokument-Generator](http://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Optionaler **String**-Parameter.<br /><br /> Überschreibt den Standardnamen der Ausgabedatei. Der Standardname wird aus dem Namen der ersten XDC-Datei abgeleitet, die verarbeitet wird.<br /><br /> Weitere Informationen finden Sie unter der **/out:** `filename`-Option im [XDCMake-Verweis](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac). Siehe Sie sich auch die **/old**- und **/Fo**-Befehlszeilenoptionen für xdcmake.exe an.|  
|**ProjectName**|Optionaler **String**-Parameter.<br /><br /> Der Name des aktuellen Projekts.|  
|**SlashOld**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn `true`, werden zusätzliche xdcmake.exe-Optionen aktiviert.<br /><br /> Weitere Informationen finden Sie unter der **/old**-Befehlszeilenoption für xdcmake.exe.|  
|**Sources**|Erforderlicher `ITaskItem[]` -Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der **/nologo**-Option im [XDCMake-Verweis](http://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
