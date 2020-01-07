---
title: 'Gewusst wie: Installieren einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404373"
---
# <a name="how-to-install-a-visualizer"></a>Gewusst wie: Installieren einer Schnellansicht
Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.

> [!NOTE]
> In UWP-apps werden nur die standardmäßigen Text-, HTML-, XML-und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>So installieren Sie eine Schnellansicht für Visual Studio 2019
  
1. Suchen Sie die dll, die die von Ihnen erstellten Schnellansicht enthält.

2. Kopieren Sie die [Debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) -dll (und ggf. alle DLLs) an einen der folgenden Speicherorte:

    - *Visualstudioinstallpath* -`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *visualstudioversion* `\Visualizers`
    
3. Kopieren Sie die zu [debuggende Seite](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) an einen der folgenden Speicherorte:

    - *Visualstudioinstallpath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *visualstudioversion* `\Visualizers\` *Framework*

    Dabei ist *Framework* beides:
    - `net2.0` für die, die die `.NET Framework`-Laufzeit ausführen.
    - `netstandard2.0` für Debug-Ausdrücke mit einer Laufzeit, die `netstandard 2.0` (`.NET Framework v4.6.1+` oder `.NET Core 2.0+`) unterstützt.
    - `netcoreapp` für die, die die `.NET Core`-Laufzeit ausführen. (unterstützt `.NET Core 2.0+`)

4. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Das Verfahren unterscheidet sich in Visual Studio 2017 und älter. Weitere Informationen finden Sie in der [vorherigen Version](how-to-install-a-visualizer.md?view=vs-2017) dieses Artikels.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>So installieren Sie eine Schnellansicht für Visual Studio 2017 und ältere

> [!IMPORTANT]
> Nur .NET Framework Visualisierungen werden in Visual Studio 2017 und älter unterstützt.

1. Suchen Sie die DLL, die die erstellte Schnellansicht enthält.

2. Kopieren Sie die DLL an einen der folgenden Speicherorte:

    - *Visualstudioinstallpath* -`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *visualstudioversion* `\Visualizers`

3. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.
::: moniker-end

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Gewusst wie: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md)
