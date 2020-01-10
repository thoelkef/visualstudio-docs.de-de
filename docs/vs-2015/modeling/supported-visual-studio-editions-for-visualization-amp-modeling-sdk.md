---
title: Unterstützte Visual Studio-Editionen für Visualisierungs-und Modellierungs-SDK | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0692efefcc92e3316ccf725c586fc6566b09a6ef
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850775"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Unterstützte Visual Studio-Editionen für die Visualisierung &amp; Modellierungs-SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im folgenden sind Listen von Visual Studio-Editionen, die mit unterstützt werden [!INCLUDE[dsl](../includes/dsl-md.md)] in der Erstellung und Bereitstellung. Weitere Informationen zu diesen Editionen finden Sie im Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Developer Center](https://msdn.microsoft.com/vstudio/products/).

## <a name="authoring-edition"></a>Erstellungsedition
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio-Visualisierungs- und Modellierungs-SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="deployment-editions"></a>Bereitstellungseditionen
 [!INCLUDE[dsl](../includes/dsl-md.md)] unterstützt die folgenden Konfigurationen für die Bereitstellung der von Ihnen erstellten domänenspezifischen Sprachen:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrierter Modus) verteilbares Paket

- Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
> Damit wird eine DSL, die auf einem Shell-Produkt ausführen können, müssen Sie festlegen der **Visual Studio-Edition unterstützt** im Erweiterungsmanifest Feld. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Siehe auch
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
