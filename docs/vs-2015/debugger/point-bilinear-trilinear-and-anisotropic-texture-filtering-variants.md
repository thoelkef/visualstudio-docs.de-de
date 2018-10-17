---
title: Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcb5c985ed91ff5c838b6555307478113af0cc2c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268282"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Punkt-, bilineare, trilineare und anisotrope Texturfiltervarianten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 In der **Punkttexturfilterung** variant, der Anwendung bereitgestellte Filtermodus durch ersetzt `D3D11_FILTER_MIN_MAG_MIP_POINT`, in der **bilineare Texturfilterung** wird es durch ersetzt `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; und klicken Sie in der **trilineare Texturfilterung** wird es durch ersetzt `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 In der **anisotrope Texturfilterung** variant, der Anwendung bereitgestellte Filtermodus durch ersetzt `D3D11_FILTER_ANISOTROPIC`, und die maximale Anisotropy auf 16 festgelegt ist.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 In Direct3D bedeutet die Funktionsebene 9.1 eine maximale Anisotropie von 2x. Da die **anisotrope Texturfilterung** Variante 16 X-Anisotropie exklusiv zu verwenden versucht, schlägt die Wiedergabe fehl, wenn die Frame-Analyse auf einer Funktionsebene 9.1-Gerät ausgeführt wird. Zu den heutigen Geräten, die von dieser Einschränkung betroffen sind, gehören die ARM-basierten Windows-Tablets Surface RT und Surface 2. Ältere GPUs, die auf einigen Computern immer noch zu finden sind, können ebenso betroffen sein, aber dies gilt hauptsächlich für Computer, die als veraltet betrachtet werden und immer weniger in Gebrauch sind.  
  
## <a name="example"></a>Beispiel  
 Die **Punkttexturfilterung** Variante reproduziert werden kann, mithilfe von Code wie folgt:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **bilineare Texturfilterung** Variante reproduziert werden kann, mithilfe von Code wie folgt:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **trilineare Texturfilterung** Variante reproduziert werden kann, mithilfe von Code wie folgt:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Beispiel  
 Die **anisotrope Texturfilterung** Variante reproduziert werden kann, mithilfe von Code wie folgt:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```



