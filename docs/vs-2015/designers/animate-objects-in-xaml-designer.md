---
title: Animieren von Objekten im XAML-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0495397ccce63b93e524c2b3898b4f18ac981ff6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230079"
---
# <a name="animate-objects-in-xaml-designer"></a>Animieren von Objekten im XAML-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können kurze Animationen erstellen, die Objekte bewegen, oder sie ein- und ausblenden.  
  
 Erstellen Sie zunächst ein *Storyboard*. Ein Storyboard enthält eine oder mehrere *Zeitachsen*. Legen Sie auf einer Zeitachse *Keyframes* fest, um Änderungen an den Eigenschaften zu markieren. Beim Ausführen der Animation interpoliert Blend dann die Eigenschaftsänderungen im festgelegten Zeitraum. Das Ergebnis ist ein reibungsloser Übergang. Sie können jede Eigenschaft animieren, die zu einem Objekt gehört, sogar nicht visuelle Eigenschaften.  
  
 Die folgende Abbildung zeigt ein Storyboard mit dem Namen **MoveUp**. Die Zeitachse enthält Keyframes, die die x- und y-Position eines Rechtecks markieren. Wenn diese Animation ausgeführt wird, wird das Rechteck nahtlos von einer Position zu einer anderen verschoben.  
  
 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")  
  
 Erfahren Sie, wie Sie Animationen erstellen können, indem Sie diese Videos ansehen.  
  
|Sehen Sie sich ein kurzes Video an (womöglich nur in englischer Sprache):|Weitere Informationen:|  
|--------------------------|-------------------|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Erstellen von Zeitachsen](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Erstellen Sie eine Zeitachse, und arbeiten Sie mit Objekten in der Zeitachse.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen von Keyframes und Wiederholen der Animation](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Fügen Sie Keyframes hinzu, und legen Sie bei jedem Keyframe Eigenschaften fest. Führen Sie dann die Animation aus, und beobachten Sie den reibungslosen Übergang von Objekten zwischen ihnen.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Hinzufügen von Ereignistriggern für Interaktivität](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Starten Sie eine Animation, wenn ein Ereignis eintritt. Starten Sie z. B. eine, wenn das Fenster geladen wird.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animieren von Farben](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Verwenden Sie eine Animation, um die Farbe eines Objekts zu ändern.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Erstellen und Ändern von Animationspfaden](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Animieren Sie Objekte entlang eines Pfads.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Übergänge bei Keyframes](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Beschleunigen oder verlangsamen Sie eine Animation am Anfang (*Hineinzoomen*) oder am Ende (*Herauszoomen*) einer Animation.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Animieren der Schaltfläche](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Erstellen Sie interessante Effekte für eine Schaltfläche, die angezeigt werden, wenn der Benutzer darauf zeigt.|  
|![Installierte Funktionen konfigurieren](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Erstellen von Animationen und Arbeiten mit Übergängen](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Animieren Sie Effekte, die angezeigt werden, wenn ein Benutzer auf die Schaltfläche in Form eines Taschenrechner-Bildes drückt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)



