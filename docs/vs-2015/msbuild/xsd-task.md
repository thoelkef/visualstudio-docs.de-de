---
title: XSD-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5a6bf91c6e9218593031ff15f2b31822ea5fa1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523145"
---
# <a name="xsd-task"></a>XSD-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [XSD-Aufgabe](https://docs.microsoft.com/visualstudio/msbuild/xsd-task).  
  
  
Umschließt das XML-Schemadefinitionstool (xsd.exe), das Schema- oder Klassendateien aus einer Quelle generiert.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **XSD**-Aufgabe beschrieben.  
  
-   **AdditionalOptions**  
  
     Optionaler **String**-Parameter.  
  
     Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: „*/option1 /option2 /option#*“. Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **XSD**-Aufgabenparameter repräsentiert werden.  
  
-   **GenerateFromSchema**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Typen an, die aus dem angegebenen Schema generiert werden.  
  
     Geben Sie einen der folgenden Werte an, von denen jeder einer XSD-Option entspricht.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Sprache**  
  
     Optionaler **String**-Parameter.  
  
     Gibt die Programmiersprache an, die für den generierten Code verwendet werden soll.  
  
     Wählen Sie zwischen **CS** (C#, der Standard), **VB** (Visual Basic) und **JS** (JScript) aus. Sie können auch einen vollqualifizierten Namen für eine Klasse angeben, die `System.CodeDom.Compiler.CodeDomProvider Class` implementiert.  
  
-   **Namespace**  
  
     Optionaler **String**-Parameter.  
  
     Gibt den Laufzeitnamespace für die generierten Typen an.  
  
-   **Sources**  
  
     Erforderlicher `ITaskItem[]` -Parameter.  
  
     Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.  
  
-   **SuppressStartupBanner**  
  
     Optionaler **Boolean**-Parameter.  
  
     Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.  
  
-   **TrackerLogDirectory**  
  
     Optionaler **String**-Parameter.  
  
     Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)



