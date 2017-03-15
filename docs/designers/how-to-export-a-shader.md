---
title: "Gewusst wie: Exportieren eines Shaders | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Gewusst wie: Exportieren eines Shaders
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dokument wird veranschaulicht, wie Sie den Shader\-Designer verwenden können, um einen Schader der Directed Graph Shader Language \(DGSL\) für die Verwendung in Ihrer App zu exportieren.  
  
 In diesem Dokument wird die folgende Aktivität veranschaulicht:  
  
-   Exportieren eines Shaders  
  
## Exportieren eines Shaders  
 Nachdem Sie einen Shader unter Verwendung des Shader\-Designers erstellt haben und bevor Sie diesen in Ihrer App verwenden können, müssen Sie ihn in einem Format exportieren, das vorn Ihrer Grafiken\-API unterstützt wird.  Sie können einen Shader auf verschiedene Weise exportieren, um verschiedene Anforderungen zu erfüllen.  
  
#### So exportieren Sie einen Shader  
  
1.  Öffnen Sie eine **Visual Shaderdiagramm \(.dgsl\)**\-Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Ist keine **Visuelles Shaderdiagramm \(.dgsl\)**\-Datei zum Öffnen vorhanden, erstellen Sie eine wie in [Gewusst wie: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md) beschrieben.  
  
2.  Klicken Sie auf der Symbolleiste **Shader\-Designer**, wählen Sie **Exportieren**, **Exportieren alsErweitert** aus.  Das Dialogfeld **Shader exportieren** wird angezeigt.  
  
3.  Wählen Sie in der Dropdownliste **Dateityp** das Format aus, das Sie exportieren möchten.  
  
     Im Folgenden finden Sie die Stile, die Sie festlegen können:  
  
     **HLSL\-Pixel\-Shader \(\*.hlsl\)**  
     Exportiert den Shader als High\-Level Shader Language \(HLSL\)\-Quellcode.  Die Option erlaubt es, den Shader später zu ändern, auch nachdem er in einer App bereitgestellt wurde.  Das kann es Ihnen das Debuggen und Patchen des Codes auf Grundlage von Endbenutzerproblemen erleichtern. Allerdings vereinfacht es Benutzern auch den Shader in unerwünschter Weise zu ändern; beispielsweise, um einen unfairen Vorteil in einem wettbewerbsfähigen Spiel zu erlangen.  Sie auch erweiterte möglicherweise die Ladezeit des Shaders.  
  
     **Kompilierter Pixel\-Shader \(\*.cso\)**  
     Exportiert den Shader in HLSL\-Bytecode.  Die Option erlaubt es, den Shader später zu ändern, auch nachdem er in einer App bereitgestellt wurde.  Das kann es Ihnen das Debuggen und Patchen des Codes auf Grundlage von Endbenutzerproblemen erleichtern. Da der Shader jedoch vorkompiliert wird, entsteht für die App beim Laden des Shaders kein zusätzlicher Laufzeit\-Mehraufwand.  Benutzer mit genug Erfahrung können den Shader zwar noch immer auf unerwünschte Weise ändern, durch Kompilieren des Shaders wird dies jedoch ungleich schwieriger.  
  
     **C\+\+\-Header \(\*.h\)**  
     Exportiert den Shader als ein Header im C\-Stil, der ein Bytearray definiert, das HLSL\-Bytecode enthält.  Durch diese Option kann das Debuggen und Patchen des Codes auf Grundlage von Endbenutzerproblemen zeitaufwändiger werden, da die App zum Testen der Lösung neu kompiliert werden muss.  Da diese Option es erschwert, wenn auch nicht unmöglich macht, den Shader zu ändern, nachdem er in einer App bereitgestellt wurde, stellt es einen Benutzer, der den Shader auf unerwünschte Weise ändern möchte, vor die größten Schwierigkeiten.  
  
4.  Geben Sie im Kombinationsfeld **Dateiname** einen Namen für den exportierten Shader ein, und wählen Sie anschließend die Schaltfläche **Speichern** aus.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines standardmäßigen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)   
 [Shader\-Designer](../designers/shader-designer.md)