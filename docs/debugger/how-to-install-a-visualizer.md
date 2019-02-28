---
title: 'Vorgehensweise: Installieren einer Schnellansicht | Microsoft-Dokumentation'
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
ms.openlocfilehash: d1a552c07443e4dd38070a86b7d9513d8cfa0136
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691422"
---
# <a name="how-to-install-a-visualizer"></a>Gewusst wie: Installieren einer Schnellansicht
Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.

> [!NOTE]
>  In UWP-apps können nur den standard-Text werden die HTML-, XML- und JSON-Schnellansichten unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.

### <a name="to-install-a-visualizer"></a>So installieren Sie eine Schnellansicht

1.  Suchen Sie die DLL, die die erstellte Schnellansicht enthält.

2.  Kopieren Sie die DLL an einen der folgenden Speicherorte:

    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    -   `My Documents\` *VisualStudioVersion* `\Visualizers`

3.  Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.

4.  Starten Sie die Debugsitzung neu.

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Gewusst wie: Schreiben einer Schnellansicht](/visualstudio/debugger/create-custom-visualizers-of-data)