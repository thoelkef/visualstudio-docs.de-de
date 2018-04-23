---
title: Zeitpunkt, bilineare, trilineare und anisotrope Texturfiltervarianten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8002a0f85d2e2e04ff061c1f156b6c8528d85d07
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten
Überschreibt den Filterungsmodus auf passenden Textursamplern.  
  
## <a name="interpretation"></a>Interpretation  
 Verschiedene Textursampling-Methoden bringen verschiedene Leistungskosten und Bildqualitäten. Folgende Filtermodi sind mit steigenden Kosten und höherer Bildqualität verbunden:  
  
1.  Punktfilterung (am günstigen, schlechteste visuelle Qualität)  
  
2.  Bilineare Filterung  
  
3.  Trilineare Filterung  
  
4.  Anisotrope Filterung (am teuersten, höchste visuelle Qualität)  
  
 Wenn die Leistungskosten jeder Variante mit intensiveren Filterungsmodi deutlich steigen, können Sie die Kosten gegen die höhere Bildqualität abwägen. Anhand dieser Bewertung können Sie dann höhere Leistungskosten für eine höhere visuelle Qualität oder eine niedrigere visuelle Qualität für eine höhere Rahmenrate oder für eine Leistung, die auf andere Weise nicht zu erreichen ist, akzeptieren.  
  
 Wenn die Leistungskosten keine Rolle spielen oder unabhängig vom Filtermodus gleich bleiben – z. B., wenn die GPU, die Sie anzielen, einen redundant hohen Shader-Durchsatz und eine hohe Bandbreite hat –, können Sie die anisotrope Filterung verwenden, um die beste Bildqualität in Ihrer App zu erreichen.  
  
## <a name="remarks"></a>Hinweise  
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
  
 In der **Punkttexturfilterung** variant, der Anwendung bereitgestellte Filtermodus durch ersetzt `D3D11_FILTER_MIN_MAG_MIP_POINT`, in der **bilineare Texturfilterung** variant, er wird durch ersetzt `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; und klicken Sie in der **trilineare Texturfilterung** variant, er wird durch ersetzt `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 In der **anisotrope Texturfilterung** variant, der Anwendung bereitgestellte Filtermodus durch ersetzt `D3D11_FILTER_ANISOTROPIC`, und die maximale Anisotropy wird auf 16 festgelegt.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 In Direct3D bedeutet die Funktionsebene 9.1 eine maximale Anisotropie von 2x. Da die **anisotrope Texturfilterung** Variante wird versucht, 16 X-Anisotropie exklusiv zu verwenden, schlägt die Wiedergabe fehl, wenn die Frame-Analyse auf einer Funktionsebene 9.1 Gerät ausgeführt wird. Zu den heutigen Geräten, die von dieser Einschränkung betroffen sind, gehören die ARM-basierten Windows-Tablets Surface RT und Surface 2. Ältere GPUs, die auf einigen Computern immer noch zu finden sind, können ebenso betroffen sein, aber dies gilt hauptsächlich für Computer, die als veraltet betrachtet werden und immer weniger in Gebrauch sind.  
  
## <a name="example"></a>Beispiel  
 Die **Punkttexturfilterung** Variante durch Verwendung eines Codes reproduziert werden kann:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **bilineare Texturfilterung** Variante durch Verwendung eines Codes reproduziert werden kann:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **trilineare Texturfilterung** Variante durch Verwendung eines Codes reproduziert werden kann:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **anisotrope Texturfilterung** Variante durch Verwendung eines Codes reproduziert werden kann:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```