---
title: Bereitgestellten Dienste (Source Control VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a52ffa7067a91582d8bfe31e09d6b03be54c4ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="services-provided-source-control-vspackage"></a>Bereitgestellten Dienste (Source Control VSPackage)
Dienste sind der primäre Mechanismus, der über dem Funktionalität unter VSPackages sowie zwischen der integrierten Entwicklungsumgebung (IDE) von Visual Studio und der installierten VSPackages gemeinsam genutzt wird. Detaillierte Beschreibung der Dienste und ihre Bedeutung in der Visual Studio-IDE finden Sie unter[verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Die Quellcodeverwaltungsdienst  
 Visual Studio bietet zwei Ebenen von Diensten, die IDE-Level-Dienste und die Paket-Level-Dienste. Der Visual Studio-IDE stellt systemintern IDE-Level-Dienste bereit. Das Quellcodeverwaltungspaket belegt einige dieser Dienste. Das Quellcodeverwaltungspaket als ein VSPackage teilt die Quellcodeverwaltungsfunktion durch einen eigenen privaten quellcodeverwaltungsdienst bereitstellen. Das Quellcodeverwaltungspaket kapselt die Gruppe von Quelle Steuerelement bezogene Schnittstellen implementiert, die von ihm in Form eines Vertrags, der von der Visual Studio-IDE verwendet werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)