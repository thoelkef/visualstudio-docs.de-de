---
title: Bereitgestellte Dienste (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705405"
---
# <a name="services-provided-source-control-vspackage"></a>Bereitgestellte Dienste (Quellcodeverwaltungs-VSPackage)
Dienste sind der primäre Mechanismus, über den die Funktionalität von VSPackages und zwischen der integrierten Visual Studio-Entwicklungsumgebung (IDE) und den installierten VSPackages gemeinsam genutzt wird. Ausführliche Beschreibungen der Dienste und ihrer Bedeutung in der Visual Studio-IDE finden Sie unter[Verwenden und Bereitstellen von Diensten](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Der Quellcodeverwaltungsdienst
 Visual Studio bietet zwei Ebenen von Diensten, Dienste auf IDE-Ebene und Dienste auf Paketebene. Die Visual Studio-IDE stellt nativ Dienste auf IDE-Ebene bereit. Das Quellcodeverwaltungspaket verbraucht einige dieser Dienste. Das Quellcodeverwaltungspaket als VSPackage teilt seine Quellcodeverwaltungsfunktionalität, indem es einen eigenen privaten Quellcodeverwaltungsdienst bereitstellt. Das Quellcodeverwaltungspaket kapselt den Satz von Quellcodeverwaltungsschnittstellen, die von ihm implementiert werden, in Form eines Vertrags, der von der Visual Studio-IDE verwendet werden kann.

## <a name="see-also"></a>Weitere Informationen
- [Entwurfselemente](../../extensibility/internals/source-control-vspackage-design-elements.md)
