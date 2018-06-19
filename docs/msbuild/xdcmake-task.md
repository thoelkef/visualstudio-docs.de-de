---
title: XSD-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dab82b3ddf2bc39d1253321a335e1fe838235819
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572321"
---
# <a name="xdcmake-task"></a>XDCMake-Aufgabe
Umschließt das XML-Dokumentationstool (xdcmake.exe), das die XML-Dokument-Kommentardateien (.xdc) in einer XML-Datei zusammengeführt.  
  
 Es wird eine XDC-Datei erstellt, wenn Sie Dokumentationskommentare in Ihren Visual C++-Quellcode eingeben und mithilfe der Compileroption [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) kompilieren. Weitere Informationen finden Sie unter [XDCMake-Verweis](/cpp/ide/xdcmake-reference), [Eigenschaftenseiten für das Tool XML-Dokument-Generator](/cpp/ide/xml-document-generator-tool-property-pages) und unter der Befehlszeilenhilfe-Option (**/?**) für xdcmake.exe.  
  
## <a name="remarks"></a>Hinweise  
 Standardmäßig unterstützt das xdcmake.exe-Tool einige Befehlszeilenoptionen. Zusätzliche Optionen werden bei der Angabe der **/old**-Befehlszeilenoption unterstützt.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **XDCMake**-Aufgabe beschrieben.  
  
|Parameter|description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Optionaler **String[]**-Parameter.<br /><br /> Gibt eine oder mehrere weitere XDC-Dateien zum Zusammenführen an.<br /><br /> Weitere Informationen finden Sie unter der Beschreibung **Zusätzliche Dokumentdateien** unter [Eigenschaftenseiten für das XML-Dokument-Generator-Tool](/cpp/ide/xml-document-generator-tool-property-pages). Sehen Sie sich auch die **/old**- und **/FS**-Befehlszeilenoptionen für xdcmake.exe an.|  
|**AdditionalOptions**|Optionaler **String**-Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: „*/option1 /option2 /option#*“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XDCMake**-Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter [XDCMake-Verweis](/cpp/ide/xdcmake-reference), [Eigenschaftenseiten für das Tool XML-Dokument-Generator](/cpp/ide/xml-document-generator-tool-property-pages) und unter der Befehlszeilenhilfe (**/?**) für xdcmake.exe.|  
|**DocumentLibraryDependencies**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn `true` und das aktuelle Projekt über eine Abhängigkeit in einem statischen Bibliotheksprojekt (.lib) in der Projektmappe verfügen, werden die XDC-Dateien für das Bibliotheksprojekt in der XML-Dateiausgabe für das aktuelle Projekt eingefügt.<br /><br /> Weitere Informationen finden Sie in der Beschreibung **Dokumentbibliothekabhängigkeiten** unter [Eigenschaftenseiten für das Tool XML-Dokument-Generator](/cpp/ide/xml-document-generator-tool-property-pages).|  
|**OutputFile**|Optionaler **String**-Parameter.<br /><br /> Überschreibt den Standardnamen der Ausgabedatei. Der Standardname wird aus dem Namen der ersten XDC-Datei abgeleitet, die verarbeitet wird.<br /><br /> Weitere Informationen finden Sie unter der **/out:** `filename`-Option im [XDCMake-Verweis](/cpp/ide/xdcmake-reference). Siehe Sie sich auch die **/old**- und **/Fo**-Befehlszeilenoptionen für xdcmake.exe an.|  
|**ProjectName**|Optionaler **String**-Parameter.<br /><br /> Der Name des aktuellen Projekts.|  
|**SlashOld**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn `true`, werden zusätzliche xdcmake.exe-Optionen aktiviert.<br /><br /> Weitere Informationen finden Sie unter der **/old**-Befehlszeilenoption für xdcmake.exe.|  
|**Sources**|Erforderlicher `ITaskItem[]` -Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der **/nologo**-Option im [XDCMake-Verweis](/cpp/ide/xdcmake-reference).|  
|**TrackerLogDirectory**|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)