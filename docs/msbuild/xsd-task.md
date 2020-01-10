---
title: XSD-Aufgabe | Microsoft-Dokumentation
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c256e02901d4f7dd7de6f14e9f650626feac25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565785"
---
# <a name="xsd-task"></a>XSD-Aufgabe
Umschließt das XML-Schemadefinitionstool (*xsd.exe*), das Schema- oder Klassendateien aus einer Quelle generiert.

> [!NOTE]
> Ab Visual Studio 2017 ist die Unterstützung von C++-Projekten für *xsd.exe* veraltet. Sie können die APIs **Microsoft.VisualC.CppCodeProvider** weiterhin verwenden, indem Sie die Datei *CppCodeProvider.dll* manuell dem globalen Assemblycache hinzufügen.

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der **XSD**-Aufgabe beschrieben.

- **AdditionalOptions**

     Optionaler **String**-Parameter.

     Eine Liste von Optionen, wie in der Befehlszeile angegeben. Zum Beispiel „/\<Option1> /\<Option2> /\<Option#>“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XSD**-Aufgabenparameter repräsentiert werden.

- **GenerateFromSchema**

  Optionaler **String**-Parameter.

  Gibt die Typen an, die aus dem angegebenen Schema generiert werden.

  Geben Sie einen der folgenden Werte an, von denen jeder einer XSD-Option entspricht.

  - **classes** -  **/classes**

  - **dataset** -  **/dataset**

- **Sprache**

     Optionaler **String**-Parameter.

     Gibt die Programmiersprache an, die für den generierten Code verwendet werden soll.

     Wählen Sie zwischen **CS** (C#, der Standard), **VB** (Visual Basic) und **JS** (JScript) aus. Sie können auch einen vollqualifizierten Namen für eine Klasse angeben, die `System.CodeDom.Compiler.CodeDomProvider Class` implementiert.

- **Namespace**

     Optionaler **String**-Parameter.

     Gibt den Laufzeitnamespace für die generierten Typen an.

- **Sources**

     Erforderlicher `ITaskItem[]` -Parameter.

     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.

- **SuppressStartupBanner**

     Optionaler **Boolean**-Parameter.

     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.

- **TrackerLogDirectory**

     Optionaler **String**-Parameter.

     Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.

## <a name="see-also"></a>Siehe auch
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
