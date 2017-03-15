---
title: "Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Überschreibt den Filterungsmodus auf passenden Textursamplern.  
  
## Interpretation  
 Verschiedene Textursampling\-Methoden bringen verschiedene Leistungskosten und Bildqualitäten.  Folgende Filtermodi sind mit steigenden Kosten und höherer Bildqualität verbunden:  
  
1.  Punktfilterung \(am günstigen, schlechteste visuelle Qualität\)  
  
2.  Bilineare Filterung  
  
3.  Trilineare Filterung  
  
4.  Anisotrope Filterung \(am teuersten, höchste visuelle Qualität\)  
  
 Wenn die Leistungskosten jeder Variante mit intensiveren Filterungsmodi deutlich steigen, können Sie die Kosten gegen die höhere Bildqualität abwägen.  Anhand dieser Bewertung können Sie dann höhere Leistungskosten für eine höhere visuelle Qualität oder eine niedrigere visuelle Qualität für eine höhere Rahmenrate oder für eine Leistung, die auf andere Weise nicht zu erreichen ist, akzeptieren.  
  
 Wenn die Leistungskosten keine Rolle spielen oder unabhängig vom Filtermodus gleich bleiben – z. B., wenn die GPU, die Sie anzielen, einen redundant hohen Shader\-Durchsatz und eine hohe Bandbreite hat –, können Sie die anisotrope Filterung verwenden, um die beste Bildqualität in Ihrer App zu erreichen.  
  
## Hinweise  
 Diese Varianten überschreiben die Samplerstatus in Aufrufen von `ID3D11DeviceContext::PSSetSamplers`, in denen eine der folgenden Filtermethoden für den von der Anwendung bereitgestellten Sampler verwendet wird:  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 In der Variante **Punkttexturfilterung** wird der von der Anwendung bereitgestellte Filtermodus durch `D3D11_FILTER_MIN_MAG_MIP_POINT` ersetzt; in der Variante **Bilineare Texturfilterung** wird er durch `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT` ersetzt; und in der Variante **Trilinearen Texturfilterung** wird er durch `D3D11_FILTER_MIN_MAG_MIP_LINEAR` ersetzt.  
  
 In der **anisotropen Texturfilterung** wird der von der Anwendung bereitgestellte Filtermodus durch `D3D11_FILTER_ANISOTROPIC` ersetzt, und die maximale Anisotropie wird auf 16 gesetzt.  
  
## Einschränkungen  
 In Direct3D bedeutet die Funktionsebene 9.1 eine maximale Anisotropie von 2x.  Da die Variante **Anisotrope Texturfilterung** versucht, die 16x\-Anisotropie exklusiv zu verwenden, schlägt die Wiedergabe fehl, wenn die Frameanalyse auf einem Gerät mit dem Funktionslevel 9.1 durchgeführt wird.  Zu den heutigen Geräten, die von dieser Einschränkung betroffen sind, gehören die ARM\-basierten Windows\-Tablets Surface RT und Surface 2.  Ältere GPUs, die auf einigen Computern immer noch zu finden sind, können ebenso betroffen sein, aber dies gilt hauptsächlich für Computer, die als veraltet betrachtet werden und immer weniger in Gebrauch sind.  
  
## Beispiel  
 Die Variante **Punkttexturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Beispiel  
 Die Variante **Bilineare Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Beispiel  
 Die Variante **Trilineare Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## Beispiel  
 Die Variante **Anisotrope Texturfilterung** kann durch Verwendung eines Codes reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```