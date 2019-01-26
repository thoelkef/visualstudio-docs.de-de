---
title: Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6bf3764d1c1e2e463406775ae11374e924b0d91f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922024"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK

Im folgenden sind Listen von Visual Studio-Editionen, die mit unterstützt werden [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in der Erstellung und Bereitstellung. Weitere Informationen zu diesen Editionen finden Sie unter Microsoft Visual Studio [Developer Center](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Erstellungsedition

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Bereitstellungseditionen

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] unterstützt die folgenden Konfigurationen für die Bereitstellung der von Ihnen erstellten domänenspezifischen Sprachen:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Visual Studio Shell (integrierter Modus) verteilbares Paket

-   Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
> Damit wird eine DSL, die auf einem Shell-Produkt ausführen können, müssen Sie festlegen der **Visual Studio-Edition unterstützt** im Erweiterungsmanifest Feld. Weitere Informationen finden Sie unter [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)