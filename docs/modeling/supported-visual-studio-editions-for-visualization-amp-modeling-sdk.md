---
title: Unterstützte Visual Studio-Editionen für Visualisierungs-und Modellierungs-SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efe452f059d7184e1f7c87fddd6bdc6c213ece8a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983729"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Unterstützte Visual Studio-Versionen für das Visualisierungs- und Modellierungs-SDK

Im folgenden finden Sie Listen der Visual Studio-Editionen, die mit [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in den Erstellungs-und Bereitstellungs Umgebungen unterstützt werden. Weitere Informationen zu diesen Editionen finden Sie im Microsoft Visual Studio [Developer Center](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Erstellungsedition

Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Bereitstellungseditionen

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] unterstützt die folgenden Konfigurationen für die Bereitstellung der von Ihnen erstellten domänenspezifischen Sprachen:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrierter Modus) verteilbares Paket Redistributable Package

- Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
> Damit eine DSL in einem shellprodukt ausgeführt werden kann, müssen Sie das **unterstützte vs Edition** -Feld im Erweiterungs Manifest festlegen. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)