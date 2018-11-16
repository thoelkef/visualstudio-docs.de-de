---
title: Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3131acfb26dc1e973314f69fab69cad46df6295
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786638"
---
# <a name="services-provided-source-control-vspackage"></a>Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dienste sind der primäre Mechanismus, über dem Funktionalität von VSPackages sowie zwischen der integrierten Entwicklungsumgebung (IDE) von Visual Studio und der installierten VSPackages gemeinsam genutzt wird. Detaillierte Beschreibung der Dienste und ihre Bedeutung in der Visual Studio-IDE, finden Sie unter[verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Die Quellcodeverwaltungsdienst  
 Visual Studio bietet zwei Ebenen von Diensten, die Dienste auf IDE-Ebene und auf Paketebene Dienste. Visual Studio-IDE bietet nativ Dienste auf IDE-Ebene. Das Quellcodeverwaltungspaket nutzt einige dieser Dienste. Der Quellcode-Verwaltungspaket als ein VSPackage teilt die Quellcodeverwaltungsfunktionen durch einen eigenen privaten quellcodeverwaltungsdienst bereitstellen. Das Quellcodeverwaltungspaket kapselt den Satz von Steuerelementen-Schnittstellen implementiert werden in Form eines Vertrags, der von Visual Studio-IDE verwendet werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)

