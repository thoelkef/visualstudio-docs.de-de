---
title: Install a UML profile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14911cda4cfc2be5fece6005a879427c10529bbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298910"
---
# <a name="install-a-uml-profile"></a>Installieren eines UML-Profils
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Visual Studio mit einem UML-Profil erweitern. Mit einem Profil können Sie den Elementen, die Sie in UML-Modellen erstellen können, Stereotypen und zusätzliche Eigenschaften hinzufügen. Welche Versionen von Visual Studio dieses Features unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Wenn Sie ein UML-Modell erhalten, das mit Profilen erstellt wurde, werden einige Eigenschaften nur dann angezeigt, wenn Sie die gleichen Profile installieren.

 Ein Profil wird in einer Visual Studio-Erweiterung verteilt. Eine Erweiterung kann auch andere Features wie z. B. Menübefehle enthalten. For more information, see [Managing Visual Studio Extensions](https://go.microsoft.com/fwlink/?LinkId=160728).

### <a name="to-install-a-uml-profile-on-your-computer"></a>So installieren Sie ein UML-Profil auf Ihrem Computer

1. Das Profil sollte Ihnen in Form einer Datei mit Visual Studio-Erweiterung (`.vsix`) übergeben worden sein. In der gleichen Datei befinden sich möglicherweise weitere Features.

     Verschieben Sie die `.vsix`-Datei an einen geeigneten Speicherort auf Ihrem Computer.

2. Doppelklicken Sie im Windows-Explorer (oder Datei-Explorer) auf die `.vsix`-Datei, oder öffnen Sie sie in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Click **Install** in the dialog box that appears.

4. To uninstall or temporarily disable the extension, open **Extension Manager** from the **Tools** menu.

### <a name="to-uninstall-or-disable-a-profile-extension"></a>So deinstallieren oder deaktivieren Sie eine Profilerweiterung

1. On the Visual Studio **Tools** menu, click **Extension Manager**.

2. Click the extension that you want to remove, and then click **Disable** or **Uninstall**.

## <a name="see-also"></a>Siehe auch
 [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md)
