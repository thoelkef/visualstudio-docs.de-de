---
title: XAML-Fehler und -Warnungen
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a263f361e28c515f1694238c4d60fdeffb95f03a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746623"
---
# <a name="xaml-errors-and-warnings"></a>XAML-Fehler und -Warnungen

Bei der Erstellung von XAML analysiert Visual Studio den Code während Sie tippen. Wenn ein Fehler erkannt wird, erscheint eine Wellenlinie in der Codezeile. Wenn Sie mit der Maus auf die Wellenlinie zeigen, erhalten Sie Informationen zu dem Fehler bzw. der Warnung. Für einige Fehler und Warnungen wird eine Glühbirne für „Schnelle Aktion“ angezeigt. Mit der Tastenkombination **STRG**+**.** werden die Optionen zum Beheben des Problems angezeigt.

## <a name="error-types"></a>Fehlertypen

Im Hintergrund analysieren mehrere Tools gleichzeitig die XAML. XAML-Fehler werden in einen der folgenden drei Typen unterteilt, je nach Tool, mit dem der Fehler erkannt wurde:

|**Fehler erkannt von**|**Fehlercodeformat**|
|--------------------------------|-----------------|
|XAML-Sprachdienst (XAML-Editor)|XLSxxxx|
|XAML-Designer|XDGxxxx|
|Bearbeiten und Fortfahren – XAML|XECxxxx|

> [!Note]
> Nicht alle Fehler/Warnungen verfügen über einen entsprechenden Code. Solche Fehler sind in der Regel Fehler des XAML-Designers.


## <a name="suppress-xaml-designer-errors"></a>Unterdrücken von XAML-Designer-Fehlern

Öffnen Sie das Dialogfeld **Optionen**, indem Sie **Extras > Optionen** und dann **Text-Editor > XAML > Sonstiges** auswählen.

Deaktivieren Sie das Kontrollkästchen **Show errors detected by the XAML designer** (Fehler anzeigen, die vom XAML-Designer erkannt wurden).

![Unterdrücken von XAML-Designer-Fehlern](../designers/media/suppress_xaml_designer_errors.png)


