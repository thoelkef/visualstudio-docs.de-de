---
title: Einschränkungen für Zeichenfolgenlängen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b989fc18ae14790b001b7eca9b403a65c0dfa9b9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716687"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen der Zeichenfolge
Die Source-Plug-in-API schränkt die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.

## <a name="string-length-values"></a>Länge-Zeichenfolgenwerten

|Konstante|Wert|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
>  Länge schließt nicht das abschließende `null`. Schließen Sie andere Konstanten mit dem Suffix "_Größe" anstelle von "_LEN" Speicherplatz für das abschließende `null`.

|Konstante|Wert|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)