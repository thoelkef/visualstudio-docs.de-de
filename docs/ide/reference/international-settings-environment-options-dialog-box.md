---
title: Internationale Einstellungen, Umgebung, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64e65894fffd9c6786c19a337fc386f45fb9d203
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540666"
---
# <a name="options-dialog-box-environment--international-settings"></a>Dialogfeld „Optionen“: Umgebung –\> Internationale Einstellungen

Auf der Seite „Internationale Einstellungen“ können Sie die Standardsprache ändern, wenn mehrere Sprachversionen der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) auf Ihrem Computer installiert sind. Sie können auf dieses Dialogfeld zugreifen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Internationale Einstellungen** auswählen.

**Sprache**

Führt alle verfügbaren Sprachen für die installierten Produktsprachversionen auf. Wenn mehrere Sprachen des Produkts oder eine gemischte Sprachinstallation von Produkten die gleiche Umgebung gemeinsam verwenden, entspricht die Sprachauswahl der **Microsoft Windows-Sprache**.

> [!CAUTION]
> In einem System mit mehreren Sprachen hat diese Einstellung keine Auswirkungen auf die Visual C++-Buildtools (cl.exe, link.exe, nmake.exe, bscmake.exe und verwandte Dateien). Diese Tools verwenden die Version für die zuletzt installierte Sprache. Die Buildtools für die zuvor installierte Sprache werden überschrieben, da die Visual C++-Buildtools nicht das DLL-Satellitenmodell verwenden.

### <a name="see-also"></a>Siehe auch

- [Installieren von Sprachpaketen](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)