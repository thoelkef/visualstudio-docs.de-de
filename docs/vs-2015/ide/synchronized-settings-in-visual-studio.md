---
title: Synchronisierte Einstellungen
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1b0ab4b0d006183f6be3c42626c022d45a2de4ce
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067128"
---
# <a name="synchronized-settings-in-visual-studio"></a>Synchronisierte Einstellungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie dasselbe Personalisierungskonto verwenden, um sich auf mehreren Computern bei Visual Studio anzumelden, werden Ihre Einstellungen standardmäßig auf allen Computern synchronisiert.

## <a name="synchronized-settings"></a>Synchronisierte Einstellungen
 Standardmäßig werden die folgenden Einstellungen synchronisiert:

-   Entwicklungseinstellungen (Sie müssen eine Reihe von Einstellungen auswählen, wenn Sie Visual Studio zum ersten Mal ausführen; die Auswahl kann jedoch jederzeit geändert werden. Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio (Anpassen der Entwicklungseinstellungen in Visual Studio)](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)

-   Im Folgenden finden Sie die Optionen auf den Seiten **Tools &#124; Optionen**:

    -   **Design** und Menüleisten-Schreibweiseneinstellungen auf der Optionsseite **Umgebung** > **Allgemein**

    -   Alle Einstellungen auf der Optionsseite **Umgebung** > **Schriftarten und Farben**

    -   Alle Tastenkombinationen auf der Optionsseite **Umgebung** > **Tastatur**

    -   Alle Einstellungen auf der Optionsseite **Umgebung, Registerkarten und Fenster**

    -   Alle Einstellungen auf der Optionsseite **Umgebung** > **Start**

    -   Alle Einstellungen auf den Optionsseiten des **Text-Editors**

-   Alle Einstellungen auf den Optionsseiten für den XAML-Designer

-   Benutzerdefinierte Befehlsaliase. Weitere Informationen zur Definition von Befehlsaliasen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

-   Benutzerdefinierte Fensterlayouts auf der Seite **Fenster &#124; Fensterlayouts verwalten**

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>Deaktivieren der synchronisierten Einstellungen für einen bestimmten Computer
 Die synchronisierten Einstellungen für Visual Studio sind standardmäßig aktiviert. Sie können die synchronisierten Einstellungen auf einem Computer deaktivieren, indem Sie zur Seite **Tools &#124; Optionen &#124; Umgebung &#124; Synchronisierte Einstellungen** wechseln und das Kontrollkästchen deaktivieren.  Angenommen, Sie möchten, dass die Einstellungen von Visual Studio auf Computer A nicht synchronisiert werden. So werden alle auf Computer A vorgenommenen Änderungen weder auf Computer B noch auf Computer C angezeigt. Computer B und Computer C nehmen weiterhin eine Synchronisierung miteinander vor, jedoch nicht mit Computer A.

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Synchronisieren von Einstellungen über die Produktfamilie und Editionen von Visual Studio hinweg
 Einstellungen können über jede Edition von Visual Studio 2015 hinweg synchronisiert werden, einschließlich der Editionen Express und Community. Einstellungen werden auch über die Visual Studio-Produktfamilie hinweg synchronisiert, beispielsweise Blend. Jedes dieser Familienprodukte weist jedoch möglicherweise eigene Einstellungen auf, die nicht für Visual Studio freigegeben werden. Beispielsweise werden für Blend spezifische Einstellungen auf Computer A für Blend auf Computer B freigegeben, jedoch nicht mit Visual Studio auf Computer A oder B.

> [!WARNING]
>  Die Einstellungen werden zwischen Visual Studio 2013 und Visual Studio 2015 nicht synchronisiert. Beim erstmaligen Öffnen von Visual Studio 2015 werden Ihre Einstellungen aus Visual Studio 2013 migriert, sie können danach aber nicht wieder zurück zu Visual Studio 2013 migriert werden.

## <a name="see-also"></a>Siehe auch
 [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
