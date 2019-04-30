---
title: 'Vorgehensweise: Ersetzen von Parametern in einer Vorlage | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c0a710bc3ad504c6654528db33b9a6698f4f7ae
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435163"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Vorgehensweise: Ersetzen von Parametern in einer Vorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Vorlagenparameter, etwa Klassennamen und Namespaces, ersetzen, wenn Sie eine Datei auf Basis einer Vorlage erstellen. Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Prozedur  
 Sie können Parameter in den Dateien einer Vorlage immer dann ersetzen, wenn Sie ein Projekt erstellen, das auf dieser Vorlage basiert. In dieser Prozedur wird erläutert, wie Sie eine Vorlage erstellen, durch die der Name eines Namespaces durch den sicheren Projektnamen ersetzt wird, wenn ein neues Projekt mit der Vorlage erstellt wird.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>So verwenden Sie einen Parameter, um einen Namespacenamen durch den Projektnamen zu ersetzen  
  
1. Fügen Sie den Parameter in eine oder mehrere Codedateien in der Vorlage ein. Zum Beispiel:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    > Vorlagenparameter werden im Format $*Parameter*$ geschrieben.  
  
2. Suchen Sie in der VSTEMPLATE-Datei der Vorlage nach dem `ProjectItem`-Element, in dem diese Datei enthalten ist.  
  
3. Legen Sie das `ReplaceParameters`-Attribut für das `ProjectItem`-Element auf `true` fest. Zum Beispiel:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem-Element (Visual Studio-Projektelementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
