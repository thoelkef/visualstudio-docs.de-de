---
title: RC-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 075b3d9201cc17537d62bbe467cc8fa6d3558c35
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773100"
---
# <a name="rc-task"></a>RC-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umschließt das Microsoft Windows-Ressourcencompilertool („rc.exe“). Die **RC**-Aufgabe kompiliert Ressourcen in eine RES-Datei, z.B. Cursors, Symbole, Bitmaps, Dialogfelder und Schriftarten. Weitere Informationen finden Sie unter „Ressourcencompiler“ auf der [MSDN](http://go.microsoft.com/fwlink/?LinkId=737)-Website.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der RC-Aufgabe beschrieben. Die meisten Aufgabenparameter und einige Parametersätze entsprechen einer Befehlszeilenoption.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Optionaler **String[]**-Parameter.<br /><br /> Fügt ein Verzeichnis zur Liste der Verzeichnisse hinzu, die nach Includedateien durchsucht werden.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/I**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**AdditionalOptions**|Optionaler **String**-Parameter.<br /><br /> Eine Liste der Befehlszeilenoptionen, z.B. **„**_/option1 /option2 /option#_“. Verwenden Sie diesen Parameter, um Befehlszeilenoptionen anzugeben, die nicht durch einen anderen **RC**-Aufgabenparameter dargestellt werden.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter den Optionen im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Kultur**|Optionaler **String**-Parameter.<br /><br /> Gibt eine lokale ID an, die die in den Ressourcen verwendete Kultur darstellt.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/l**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**IgnoreStandardIncludePath**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn dieser `true` ist, wird verhindert, dass der Ressourcencompiler die INCLUDE-Umgebungsvariable überprüft, wenn nach Header- oder Ressourcendateien gesucht wird.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/x**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**NullTerminateStrings**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn dieser `true` ist, lässt er alle Zeichenfolgen in der Zeichenfolgentabelle auf NULL enden.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/n**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**PreprocessorDefinitions**|Optionaler **String[]**-Parameter.<br /><br /> Definieren Sie ein oder mehrere Präprozessorsymbole für den Ressourcencompiler. Geben Sie eine Liste von Makrosymbolen an.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/d**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730). Weitere Informationen finden Sie ebenfalls unter **UndefinePreprocessorDefinitions** in dieser Tabelle.|  
|**ResourceOutputFileName**|Optionaler **String**-Parameter.<br /><br /> Gibt den Namen der Ressourcendatei an. Geben Sie einen Namen für die Ressourcendatei an.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/fo**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**ShowProgress**|Optionaler **Boolean**-Parameter.<br /><br /> Wenn dieser `true` ist, werden Meldungen angezeigt, die über den Fortschritt des Compilers berichten.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/v**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730).|  
|**Quelle**|Erforderlicher `ITaskItem[]` -Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **Boolean**-Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Geben Sie für weitere Informationen die Befehlszeilenoption **/?** ein, und klicken Sie auf die Option **/nologo**.|  
|**TrackerLogDirectory**|Optionaler **String**-Parameter.<br /><br /> Gibt das Verzeichnis des Nachverfolgungsprotokolls an.|  
|**UndefinePreprocessorDefinitions**|Hebt ein Präprozessorsymbol auf.<br /><br /> Weitere Informationen finden Sie auf der MSDN-Website unter der **/u**-Option im Artikel [Using RC (The RC Command Line) (Verwenden von RC (RC-Befehlszeile))](http://go.microsoft.com/fwlink/?LinkId=155730). Weitere Informationen finden Sie ebenfalls unter **PreprocessorDefinitions** in dieser Tabelle.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
