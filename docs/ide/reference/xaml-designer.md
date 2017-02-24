---
title: Optionen, XAML-Designer | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
ms.assetid: ad3820b2-0d95-4807-a75c-c3467ed973a3
caps.latest.revision: 1
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7c944afe8c89b8a5e30bf1e5937e848e078954ac
ms.openlocfilehash: f4a4832e5659a46b236cdcf9ff2eecdc3cabf57d

---
# <a name="options-xaml-designer"></a>Optionen, XAML-Designer
Sie verwenden die **XAML-Designer**-Eigenschaftenseite, um anzugeben, wie Elemente und Attribute in XAML-Dokumenten formatiert werden. Zum Öffnen des Dialogfelds **Optionen** wählen Sie im Menü **Extras** den Befehl **Optionen** aus. Für den Zugriff auf die Eigenschaftenseite **XAML-Designer** wählen Sie den Knoten **XAML-Designer** aus. Einstellungen für den XAML-Designer werden angewendet, wenn Sie das Dokument öffnen. Wenn Sie die Einstellungen also ändern, müssen Sie Visual Studio schließen und wieder öffnen, damit die Änderungen angezeigt werden.

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  

## <a name="enable-xaml-designer"></a>XAML-Designer aktivieren
Ist diese Einstellung ausgewählt, wird der XAML-Designer aktiviert. Der XAML-Designer bietet einen visuellen Arbeitsbereich zum Bearbeiten von XAML-Dokumenten. Für bestimmte Funktionen in Visual Studio wie IntelliSense für Ressourcen und Datenbindung muss der XAML-Designer aktiviert werden.

Die folgenden Einstellungen gelten nur, wenn der XAML-Designer aktiviert ist. Wenn Sie diese Option ändern, müssen Sie Visual Studio neu starten, damit die Einstellung wirksam wird.

## <a name="default-document-view"></a>Standarddokumentansicht
Mit dieser Einstellung wird gesteuert, ob die Entwurfsansicht angezeigt wird, wenn XAML-Dokumente geladen werden.

|||  
|-|-|  
|**Quellansicht**|Gibt an, ob nur die XAML-Quelle in der XAML-Ansicht angezeigt wird. Dies ist beim Laden großer Dokumente hilfreich.|  
|**Entwurfsansicht**|Gibt an, ob nur der visuelle XAML-Designer in der XAML-Ansicht angezeigt wird.|  
|**Geteilte Ansicht**|Gibt an, ob visueller XAML-Designer und XAML-Quelle in der XAML-Ansicht nebeneinander angezeigt werden (Ort basiert auf der Einstellung **Ausrichtung teilen**).|  

## <a name="split-orientation"></a>Ausrichtung teilen
Mit dieser Einstellung wird gesteuert, wann und wie der XAML-Designer beim Bearbeiten eines XAML-Dokuments angezeigt wird. Diese Einstellungen gelten nur, wenn **Standarddokumentansicht** auf **Geteilte Ansicht** festgelegt ist.

|||  
|-|-|  
|**Vertikal**|Auf der linken Seite der XAML-Ansicht wird die XAML-Quelle angezeigt, der XAML-Designer auf der anderen Seite.|  
|**Horizontal**|Oben in der XAML-Ansicht wird der XAML-Designer angezeigt, die XAML-Quelle darunter.|  
|**Default**|Das XAML-Dokument nutzt die geteilte Ausrichtung, die für die Plattform empfohlen wird, die das Projekt des Dokuments zum Ziel hat. Für die meisten Plattformen ist dies **Horizontal**.|  

## <a name="zoom-by-using"></a>Zoomen durch Verwendung von
Mit dieser Einstellung wird bestimmt, wie das Zoomen beim Bearbeiten eines XAML-Dokuments funktioniert.

|||  
|-|-|  
|**Mausrad**|Sie vergrößern die Ansicht im XAML-Designer, indem Sie das Mausrad drehen.|  
|**STRG+Mausrad**|Sie vergrößern die Ansicht im XAML-Designer, indem Sie die STRG-Taste drücken, während Sie das Mausrad drehen.|  
|**Alt+Mausrad**|Sie vergrößern die Ansicht im XAML-Designer, indem Sie die ALT-Taste drücken, während Sie das Mausrad drehen.|  

Diese Einstellungen bestimmen das Designer-Verhalten beim Bearbeiten eines XAML-Dokuments.

|||  
|-|-|  
|**Interaktive Elemente beim Erstellen automatisch benennen**|Gibt an, ob beim Hinzufügen eines neuen interaktiven Elements zum Designer ein Standardname für das Element bereitgestellt wird.|  
|**Layouteigenschaften bei Elementerstellung automatisch einfügen**|Gibt an, ob beim Hinzufügen eines neuen Elements zum Designer Layouteigenschaften für das Element bereitgestellt werden.|  
|**Quadrantbasiertes Layout verwenden**|Gibt an, ob das momentan ausgewählte Steuerelement an den nächstgelegenen Kanten des übergeordneten Containers ausgerichtet wird. Ist dieses Kontrollkästchen deaktiviert, werden die Steuerelementausrichtungen während des Verschiebens oder Erstellens nicht geändert.|  
|**Toolboxelemente automatisch ausfüllen**|Gibt an, ob Benutzersteuerelemente und benutzerdefinierte Steuerelemente in der aktuellen Projektmappe automatisch in der Toolbox angezeigt werden.|  

## <a name="settings-blend-only"></a>Einstellungen (nur in Blend)
Verwenden Sie diese Optionen, um beim Bearbeiten von XAML-Dateien mit Blend die Einstellungen zu bestimmen.

|||  
|-|-|  
|**Zoomen durch Verwendung von**|Sie vergrößern die Ansicht im XAML-Designer, indem Sie das Mausrad drehen, oder indem Sie die STRG-Taste bzw. die ALT-Taste drücken, während Sie das Mausrad drehen.|  
|**Texteinheiten**|Gibt an, ob Messungen im Designer auf Punkten oder Pixeln basieren. Da universelle Windows-Apps keine Punkte unterstützen, werden die Einheiten automatisch in Pixel konvertiert, falls **Punkt** ausgewählt ist.|  

## <a name="artboard-blend-only"></a>Zeichenfläche (nur in Blend)
Mit dieser Einstellungen bestimmen Sie das XAML-Designer-Verhalten beim Bearbeiten von XAML-Dokumenten in Blend.

### <a name="snapping"></a>Andocken

|||  
|-|-|  
|**Ausrichtungsgitter anzeigen**|Wird diese Option ausgewählt, werden im Designer Gitternetzlinien angezeigt, an denen Sie Steuerelemente ausrichten können. Zum Designer hinzugefügte Steuerelemente richten sich an diesen Gitternetzlinien aus, wenn die Option **An Gitternetzlinie ausrichten** ausgewählt ist.|  
|**An Gitternetzlinie ausrichten**|Werden Steuerelemente zum Designer hinzugefügt oder darin verschoben, werden sie an den Gitternetzlinien ausgerichtet.|  
|**Gitterlinienabstand**|Legt den Abstand zwischen den Gitternetzlinien in Pixeln oder Punkten fest (entsprechend der **Texteinheiten**-Einstellung).|  
|**An Ausrichtungslinien ausrichten**|Gibt an, ob Steuerelemente an Ausrichtungslinien ausgerichtet werden.|  
|**Standardrand**|Ist **An Ausrichtungslinien ausrichten** aktiviert, legt diese Option den Abstand zwischen dem Steuerelement und den Ausrichtungslinien in Pixeln oder Punkten fest (entsprechend der **Texteinheiten**-Einstellung).|  
|**Standardinnenabstand**|Ist **An Ausrichtungslinien ausrichten** aktiviert, legt diese Option zusätzlichen Leerraum zwischen dem Steuerelement und den Ausrichtungslinien in Pixeln oder Punkten fest (entsprechend der **Texteinheiten**-Einstellung).|  

### <a name="animation"></a>Animation
Mit dieser Einstellung wird bestimmt, ob eine Warnung angezeigt wird, wenn abhängige (nicht beschleunigte) Animationen in Blend aktiviert werden.

### <a name="effects"></a>Effekte
Mit diesen Einstellungen wird bestimmt, ob die Effekte gerendert werden, wenn XAML-Dateien im XAML-Designer mit Blend bearbeitet werden.

|||  
|-|-|  
|**Rendereffekte**|Gibt an, ob Effekte gerendert werden, wenn XAML-Dateien im XAML-Designer mit Blend bearbeitet werden.|  
|**Zoomschwellenwert**|Gibt den Prozentsatz für den Zoomfaktor an, mit dem Effekte gerendert werden, wenn das Kontrollkästchen **Effekte rendern** aktiviert ist. Wenn Sie über diese Einstellung hinaus vergrößern, können Effekte im XAML-Designer nicht mehr gerendert werden.|  

## <a name="see-also"></a>Siehe auch  
 [XAML in WPF](http://msdn.microsoft.com/Library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)   
 [Gewusst wie: Ändern von XAML-Ansichtseinstellungen](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [Exemplarische Vorgehensweisen zu XAML und Code](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)



<!--HONumber=Feb17_HO4-->


