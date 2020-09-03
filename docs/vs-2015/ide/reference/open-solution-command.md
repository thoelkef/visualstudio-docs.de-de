---
title: Befehl „Projektmappe öffnen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9c9ab66d2885137e9c470f577996ab861b554d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671907"
---
# <a name="open-solution-command"></a>Befehl "Projektmappe öffnen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öffnet eine vorhandene Projektmappe und schließt alle anderen geöffneten Projektmappen.

## <a name="syntax"></a>Syntax

```
File.OpenSolution filename
```

## <a name="arguments"></a>Argumente
 `Filename` ist erforderlich. Der vollständige Pfad und Dateiname der zu öffnenden Projektmappe.

 Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.

## <a name="remarks"></a>Bemerkungen
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird die Projektmappe „Test1.sln“ geöffnet.

```
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"
```

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
