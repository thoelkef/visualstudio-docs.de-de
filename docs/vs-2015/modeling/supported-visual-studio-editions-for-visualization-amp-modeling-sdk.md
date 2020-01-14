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
ms.openlocfilehash: 227c2871f68545c9f9fe5fa1ea3ceee827ccdc6a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917305"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Unterstützte Visual Studio-Editionen für die Visualisierung &amp; Modellierungs-SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im folgenden sind Listen von Visual Studio-Editionen, die mit unterstützt werden [!INCLUDE[dsl](../includes/dsl-md.md)] in der Erstellung und Bereitstellung. Weitere Informationen zu diesen Editionen finden Sie im Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Developer Center](https://msdn.microsoft.com/vstudio/products/).

## <a name="authoring-edition"></a>Erstellungsedition
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio-Visualisierungs- und Modellierungs-SDK|[Modellierungs-SDK-Download](https://www.microsoft.com/download/details.aspx?id=48148)|
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
