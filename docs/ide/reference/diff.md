---
title: -Diff („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654516"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Vergleicht zwei Dateien. Die Unterschiede werden in einem speziellen Visual Studio-Fenster angezeigt.

## <a name="syntax"></a>Syntax

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumente

- *SourceFile*

  Erforderlich. Der vollständige Pfad und der Name der ersten zu vergleichenden Datei

- *TargetFile*

  Erforderlich. Der vollständige Pfad und der Name der zweiten zu vergleichenden Datei.

- *SourceDisplayName*

  Optional. Der Anzeigename der ersten Datei

- *TargetDisplayName*

  Optional. Der Anzeigename der zweiten Datei

## <a name="remarks"></a>Anmerkungen

Wenn bereits eine Instanz der IDE geöffnet ist, wird der Dateivergleich auf einer Registerkarte in der aktuellen IDE angezeigt.

## <a name="example"></a>Beispiel

Im ersten Beispiel werden zwei Dateien ohne Änderung ihrer Anzeigenamen verglichen. Im zweiten Beispiel werden die Dateien verglichen und dabei beide Anzeigenamen geändert. Im dritten und vierten Beispiel werden zwei Dateien verglichen, doch wird ein Alias nur auf die erste Datei bzw. nur auf die zweite Datei angewendet.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Siehe auch

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
