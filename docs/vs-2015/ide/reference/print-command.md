---
title: Befehl „Drucken“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662156"
---
# <a name="print-command"></a>Befehl "Drucken"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wertet einen Ausdruck aus oder zeigt angegebenen Text an

## <a name="syntax"></a>Syntax

```
Debug.Print text
```

## <a name="arguments"></a>Argumente
 `text` ist erforderlich. Der auszuwertende Ausdruck oder der anzuzeigende Text

## <a name="remarks"></a>Bemerkungen
 Sie können ein Fragezeichen (?) als Alias für diesen Befehl verwenden. Daher wird mit dem Befehl

```
>Debug.Print expA
```

 kann beispielsweise auch folgendermaßen geschrieben werden:

```
>? expA
```

 Beide Versionen dieses Befehls geben den aktuellen Wert des Ausdrucks `expA` zurück.

## <a name="example"></a>Beispiel

```
>Debug.Print varA
```

## <a name="see-also"></a>Weitere Informationen
 Befehl " [Anweisung auswerten"](../../ide/reference/evaluate-statement-command.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
