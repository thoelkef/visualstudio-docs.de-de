---
title: 'Vorgehensweise: Öffnen mehrerer Projektmappen'
description: Erfahren Sie, wie Sie in Visual Studio für Mac mehrere Projektmappen und mehrere Instanzen der Anwendung öffnen.
author: asb3993
ms.author: amburns
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 85d300c5131dad2d6f4480fceb4770e2e8a126a5
ms.sourcegitcommit: b544e2157ac20866baf158eef9cfed3e3f1d68b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2018
ms.locfileid: "39388492"
---
# <a name="opening-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Öffnen mehrerer Projektmappen oder Instanzen von Visual Studio für Mac

Standardmäßig handelt es sich bei sämtlichen Anwendungen auf einem Mac, einschließlich Visual Studio für Mac, um Apps mit _einfachen Instanzen_. Wenn die zu verwendende Anwendung bereits geöffnet ist (dargestellt durch einen „Punkt“ unter dem Symbol im Dock), wird folglich anstelle einer neuen Instanz die ausgeführte Instanz geöffnet, wenn Sie erneut auf das Symbol klicken.  Wenn zusätzliche Instanzen der Anwendung erforderlich sind, können Sie das System dazu auffordern, diese für Sie zu öffnen, wie im [nächsten Abschnitt](#open-a-second-instance-of-visual-studio-for-mac) beschrieben wird.

Darüber hinaus wird eine Projektmappe standardmäßig in einem neuen Arbeitsbereich geöffnet, wenn Sie diese öffnen, und der aktuelle Arbeitsbereich wird (falls erforderlich) geschlossen. Sie können dieses Standardverhalten außer Kraft setzen, indem Sie den aktuellen Arbeitsbereich geöffnet lassen, wie im Abschnitt [Öffnen einer zweiten Projektmappe](#open-a-second-solution-inside-a-single-instance) beschrieben wird.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Öffnen einer zweiten Instanz von Visual Studio für Mac

Wenn Sie eine zweite Instanz der IDE öffnen möchten, müssen Sie hierzu die Anwendung **Terminal** öffnen und folgende Zeile eingeben:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Öffnen einer zweiten Projektmappe in einer einfachen Instanz

Führen Sie die folgenden Schritte aus, wenn Sie zusätzlich zu Ihrer ersten Projektmappe eine zweite Projektmappe öffnen möchten:

1. Wählen Sie **Datei > Öffnen** aus, wenn Ihre erste Projektmappe bereits geöffnet ist.
2. Durchsuchen Sie das Dateisystem, um die vorhandenen Lösung zu finden.
3. Wählen Sie die **SLN**-Datei aus, und klicken Sie auf die Schaltfläche **Optionen**:
    
    ![Position der Schaltfläche „Optionen“](media/open-multiple-solutions-image3.png)
4. Deaktivieren Sie das Kontrollkästchen **Aktuellen Arbeitsbereich schließen**:

    ![Screenshot des aktuellen Arbeitsbereichs](media/open-multiple-solutions-image1.png)

1. Klicken Sie auf die Schaltfläche „Öffnen“, um die zweite Projektmappe im Projektmappen-Explorer zu öffnen.

**Alternativ** können Sie auch die folgenden Schritte ausführen, wenn Sie die Projektmappe kürzlich geöffnet haben:

1. Wechseln Sie zum Menüelement „Datei“ > „Zuletzt verwendete Projektmappen“:

    ![Screenshot des Menüs „Zuletzt verwendete Projektmappen“](media/open-multiple-solutions-image2.png)

1. Halten Sie die **STRG**-Taste gedrückt, und wählen Sie die Projektmappe aus. Durch diese Kombination wird die zweite Projektmappe im Lösungspad geöffnet.
