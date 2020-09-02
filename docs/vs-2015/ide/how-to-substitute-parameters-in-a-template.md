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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fe49c928ca3de318410eba56afeae6f4329efed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670662"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Gewusst wie: Ersetzen von Parametern in einer Vorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Vorlagenparameter, etwa Klassennamen und Namespaces, ersetzen, wenn Sie eine Datei auf Basis einer Vorlage erstellen. Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

## <a name="procedure"></a>Prozedur
 Sie können Parameter in den Dateien einer Vorlage immer dann ersetzen, wenn Sie ein Projekt erstellen, das auf dieser Vorlage basiert. In dieser Prozedur wird erläutert, wie Sie eine Vorlage erstellen, durch die der Name eines Namespaces durch den sicheren Projektnamen ersetzt wird, wenn ein neues Projekt mit der Vorlage erstellt wird.

#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>So verwenden Sie einen Parameter, um einen Namespacenamen durch den Projektnamen zu ersetzen

1. Fügen Sie den Parameter in eine oder mehrere Codedateien in der Vorlage ein. Beispiel:

    ```
    namespace $safeprojectname$
    ```

    > [!NOTE]
    > Vorlagenparameter werden im Format $*Parameter*$ geschrieben.

2. Suchen Sie in der VSTEMPLATE-Datei der Vorlage nach dem `ProjectItem`-Element, in dem diese Datei enthalten ist.

3. Legen Sie das `ReplaceParameters`-Attribut für das `ProjectItem`-Element auf `true` fest. Beispiel:

    ```
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md) Vorlagen [Parametern](../ide/template-parameters.md) [Visual Studio-Vorlagen Schema Referenz](../extensibility/visual-studio-template-schema-reference.md) [ProjectItem-Element (Visual Studio-Element Vorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
