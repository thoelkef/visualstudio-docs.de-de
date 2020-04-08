---
title: 'Gewusst wie: Installieren eines Visualizers | Microsoft Docs'
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880259"
---
# <a name="how-to-install-a-visualizer"></a>Gewusst wie: Installieren einer Schnellansicht
Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.

> [!NOTE]
> In UWP-Apps werden nur die Standard-Text-, HTML-, XML- und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>So installieren Sie eine Visualisierung für Visual Studio 2019
  
1. Suchen Sie die DLL, die die von Ihnen erstellte Visualisierung enthält.

   In der Regel ist es am besten, wenn sowohl die Debugger-seitige DLL als auch die Debuggee-seitige DLL **eine beliebige CPU** als Zielplattform angeben. Die Debugger-seitige DLL muss entweder **beliebige CPU** oder **32-Bit**sein. Die Zielplattform für die Debuggee-seitige DLL sollte dem Debugee-Prozess entsprechen.

2. Kopieren Sie die [Debugger-Seiten-DLL](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (und alle DLLs, von denen sie abhängt) an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Kopieren Sie die [Debuggee-Seiten-DLL](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath-Framework* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework*

    wobei *Framework* entweder:
    - `net2.0`für Debuggees, `.NET Framework` die die Laufzeit ausführen.
    - `netstandard2.0`für Debuggees, die eine `netstandard 2.0` `.NET Framework v4.6.1+` Laufzeit `.NET Core 2.0+`verwenden, die ( oder ) unterstützt.
    - `netcoreapp`für Debuggees, `.NET Core` die die Laufzeit ausführen. (unterstützt `.NET Core 2.0+`)

4. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Die Prozedur ist in Visual Studio 2017 und älter anders. Siehe die [vorherige Version](how-to-install-a-visualizer.md?view=vs-2017) dieses Artikels.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>So installieren Sie eine Visualisierung für Visual Studio 2017 und älter

> [!IMPORTANT]
> Nur .NET Framework-Visualisierungen werden in Visual Studio 2017 und älter unterstützt.

1. Suchen Sie die DLL, die die erstellte Schnellansicht enthält.

2. Kopieren Sie die DLL an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.
::: moniker-end

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Gewusst wie: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md)
