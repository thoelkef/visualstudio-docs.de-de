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
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547653"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Unterstützte Visual Studio-Editionen für Visualisierungs &amp; Modellierungs-SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im folgenden finden Sie Listen der Visual Studio-Editionen, die von [!INCLUDE[dsl](../includes/dsl-md.md)] in den Erstellungs-und Bereitstellungs Umgebungen unterstützt werden. Weitere Informationen zu diesen Editionen finden Sie im Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Developer Center](https://msdn.microsoft.com/vstudio/products/).

## <a name="authoring-edition"></a>Erstellungsedition
 Zur Definition einer DSL müssen folgende Komponenten installiert sein:

|Produkt|Downloadlink|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Visualization and Modeling SDK|[Modellierungs-SDK-Download](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Bereitstellungseditionen
 [!INCLUDE[dsl](../includes/dsl-md.md)] von werden die folgenden Konfigurationen für die Bereitstellung der domänenspezifischen Sprachen unterstützt, die Sie erstellen:

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell (integrierter Modus), verteilbares Paket

- Visual Studio Shell (isolierter Modus), verteilbares Paket

> [!NOTE]
> Damit eine DSL in einem shellprodukt ausgeführt werden kann, müssen Sie das **unterstützte vs Edition** -Feld im Erweiterungs Manifest festlegen. Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
