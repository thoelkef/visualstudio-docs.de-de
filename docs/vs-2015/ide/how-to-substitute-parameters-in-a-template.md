---
title: 'Vorgehensweise: Ersetzen von Parametern in einer Vorlage | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e7e3fea66b23d86378ff4afb81a7d4f46f5090d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520392"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Gewusst wie: Ersetzen von Parametern in einer Vorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](https://docs.microsoft.com/visualstudio/ide/how-to-substitute-parameters-in-a-template).  
  
Sie können Vorlagenparameter, etwa Klassennamen und Namespaces, ersetzen, wenn Sie eine Datei auf Basis einer Vorlage erstellen. Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Prozedur  
 Sie können Parameter in den Dateien einer Vorlage immer dann ersetzen, wenn Sie ein Projekt erstellen, das auf dieser Vorlage basiert. In dieser Prozedur wird erläutert, wie Sie eine Vorlage erstellen, durch die der Name eines Namespaces durch den sicheren Projektnamen ersetzt wird, wenn ein neues Projekt mit der Vorlage erstellt wird.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>So verwenden Sie einen Parameter, um einen Namespacenamen durch den Projektnamen zu ersetzen  
  
1.  Fügen Sie den Parameter in eine oder mehrere Codedateien in der Vorlage ein. Zum Beispiel:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Vorlagenparameter werden im Format $*Parameter*$ geschrieben.  
  
2.  Suchen Sie in der VSTEMPLATE-Datei der Vorlage nach dem `ProjectItem`-Element, in dem diese Datei enthalten ist.  
  
3.  Legen Sie das `ReplaceParameters`-Attribut für das `ProjectItem`-Element auf `true` fest. Zum Beispiel:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem-Element (Visual Studio-Projektelementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)



