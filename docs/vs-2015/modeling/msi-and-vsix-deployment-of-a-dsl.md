---
title: VSIX-Bereitstellung einer DSL | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916545"
---
# <a name="vsix-deployment-of-a-dsl"></a>VSIX-Bereitstellung einer DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine domänenspezifische Sprache auf Ihrem eigenen Computer oder auf anderen Computern installieren. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] müssen bereits auf dem Zielcomputer installiert sein.

## <a name="Installing"></a>Installieren und Deinstallieren einer DSL mithilfe von VSX
 Wenn die DSL durch diese Methode installiert wird, kann der Benutzer eine DSL-Datei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]öffnen, aber die Datei kann nicht aus Windows-Explorer geöffnet werden.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>So installieren Sie eine DSL mithilfe der VSIX

1. Suchen Sie auf Ihrem Computer die **VSIX** -Datei, die von Ihrem DSL-Paket Projekt erstellt wurde.

    1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt **dslpackage** , und klicken Sie dann auf **Ordner in Windows-Explorer öffnen**.

    2. Suchen Sie den Datei- **bin\\\*\\** _yourproject_ **. Dslpackage. vsix**

2. Kopieren Sie die **VSIX** -Datei auf den Zielcomputer, auf dem Sie die DSL installieren möchten. Dies kann Ihr eigener Computer oder ein anderer Computer sein.

    - Der Zielcomputer muss über eine der Editionen von [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] verfügen, von denen DSLs zur Laufzeit unterstützt werden. Weitere Informationen finden Sie [unter Unterstützte Visual Studio-Editionen für die Visualisierung & Modellierungs-SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Auf dem Zielcomputer muss eine der Editionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in **DslPackage\source.Extensions.Manifest**angegeben sein.

3. Doppelklicken Sie auf dem Zielcomputer auf die **VSIX** -Datei.

     **Installer für Visual Studio-Erweiterungen** wird geöffnet, und die Erweiterung wird installiert.

4. Starten Sie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], bzw. starten Sie die Anwendung neu.

5. Um die DSL zu testen, verwenden Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], um eine neue Datei mit der Erweiterung zu erstellen, die Sie für Ihre DSL definiert haben.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>So deinstallieren Sie eine mit VSX installierte DSL

1. Klicken Sie **im Menü Extras** auf **Erweiterungs-Manager**.

2. Erweitern Sie **Installierte Erweiterungen**.

3. Wählen Sie die Erweiterung aus, in der die DSL definiert ist, und klicken Sie dann auf **deinstallieren**.

   In seltenen Fällen kann es vorkommen, dass eine fehlerhafte Erweiterung nicht geladen und ein Bericht im Fehlerfenster erstellt wird, aber im Erweiterungs-Manager keine Informationen angezeigt werden. Sie haben die Möglichkeit, die Erweiterung zu entfernen, indem Sie die Datei aus dem folgenden Ordner löschen:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
