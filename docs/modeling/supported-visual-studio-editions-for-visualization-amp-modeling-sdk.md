---
title: Visual Studio-Editionen für die Visualisierung unterstützt &amp; Modellierungs-SDKS
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 004a6b75bb66ebf3c1797abac9c1cc6f7faa6eb9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948193"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Visual Studio-Editionen für die Visualisierung unterstützt &amp; Modellierungs-SDKS
Im folgenden sind Listen von Visual Studio-Editionen, die mit unterstützt werden [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in der Konfiguration und Bereitstellung-Umgebungen. Weitere Informationen zu diesen Editionen finden Sie im Microsoft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [Developer Center](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Erstellungsedition
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Bereitstellungseditionen
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] unterstützt die folgenden Konfigurationen für die Bereitstellung der von Ihnen erstellten domänenspezifischen Sprachen:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Visual Studio Shell (integrierter Modus) redistributable Package redistributable-Paket

-   Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
>  Um eine DSL kann auf ein Shell-Produkt ausgeführt zu machen, müssen Sie festlegen der **VS-Edition unterstützt** -Feld in der Erweiterung Manifest. Weitere Informationen finden Sie unter [Bereitstellen einer domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Siehe auch

- [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
