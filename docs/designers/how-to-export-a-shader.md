---
title: 'Gewusst wie: Exportieren eines Shaders'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 632cd61d3844dc6f405090081ef76e5a2d6967b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924994"
---
# <a name="how-to-export-a-shader"></a>Gewusst wie: Exportieren eines Shaders
In diesem Dokument wird gezeigt, wie der Shader-Designer zum Exportieren eines Shaders der Directed Graph Shader Language (DGSL) verwendet wird, damit Sie ihn in Ihrer Anwendung verwenden können.

 In diesem Dokument wird die folgende Aktivität veranschaulicht:

-   Exportieren eines Shaders

## <a name="exporting-a-shader"></a>Exportieren eines Shaders
 Nachdem Sie einen Shader mithilfe des Shader-Designers erstellt haben, und bevor Sie ihn in Ihrer Anwendung verwenden können, müssen Sie den Shader in einem Format exportieren, das Ihre Grafik-API versteht. Sie können einen Shader auf unterschiedliche Weisen für andere Anforderungen exportieren.

#### <a name="to-export-a-shader"></a>So exportieren Sie einen Shader

1.  Öffnen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Datei **Visual Shader-Diagramm (.dgsl)**

     Wenn Sie keine Datei **Visual Shader Graph (.dgsl)** zum Öffnen haben, erstellen Sie eine, wie es unter [Vorgehensweise: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md) beschrieben wird.

2.  Klicken Sie auf der Symbolleiste **Shader-Designer** auf **Erweitert** > **Exportieren** > **Exportieren als**. Das Dialogfeld **Shader exportieren** wird angezeigt.

3.  Wählen Sie in der Dropdownliste **Dateityp** das Format aus, in das Sie exportieren möchten.

     Sie können die folgende Formate auswählen:

     **HLSL-Pixelshader (\*.hlsl):** Exportiert den Shader als HLSL-Quellcode (High Level Shader Language). Diese Option ermöglicht es, den Shader später zu ändern, auch nachdem er in einer Anwendung bereitgestellt wird. Dies kann das Debuggen und Patchen des Codes aufgrund der Probleme bei dem Endbenutzer vereinfachen, erleichtert es dem Benutzer aber genau so Ihren Shader auf ungewünschter Weise zu verändern, z.B. um einen unfairen Vorteil in einem wetteifernden Spiel zu erhalten. Es kann auch die Ladezeiten des Shaders erhöhen.

     **Kompilierter Pixelshader (\*.cso):** Exportiert den Shader als HLSL-Bytecode. Diese Option ermöglicht es, den Shader später ändern, auch nachdem er in einer Anwendung bereitgestellt wird. Dies erleichtert das Debuggen und Patchen des Codes aufgrund der Probleme beim Endbenutzer. Da der Shader jedoch vorkompiliert ist, verursacht es keinen zusätzlichen Mehraufwand bei der Laufzeit, wenn der Shader von der Anwendung geladen wird. Ausreichend erfahrene Benutzer können weiterhin den Shader auf unerwünschter Weise ändern, aber das Kompilieren des Shaders erschwert das Ganze erheblich.

     **C++-Header (\*.h):** Exportiert den Shader als Header im C-Stil, der ein Bytearray definiert, das HLSL-Bytecode enthält. Diese Option kann das Debuggen und Patchen des Codes aufgrund der Probleme beim Endnutzer zeitaufwändiger gestalten, da die App erneut kompiliert werden muss, um den Fix zu testen. Da diese Option es jedoch schwierig, aber nicht unmöglich macht, den Shader nach seiner Bereitstellung in einer App zu verändern, bereitet es für einen Benutzer, der den Shader auf unerwünschte Weise verändern möchte, die meisten Probleme.

4.  Geben Sie im Kombinationsfeld **Dateiname** einen Namen für den exportierten Shader an, und klicken Sie auf die Schaltfläche **Speichern**

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)
- [Shader-Designer](../designers/shader-designer.md)