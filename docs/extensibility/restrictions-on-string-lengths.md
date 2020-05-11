---
title: Einschränkungen für Stringlängen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701481"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen für Zeichenfolgenlängen
Die Quellcodeverwaltungs-Plug-In-API begrenzt die Längen von Zeichenfolgen, die in verschiedenen Funktionen verwendet werden.

## <a name="string-length-values"></a>Stringlängenwerte

|Konstante|Wert|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Die Länge umfasst nicht `null`die beendende . Andere Konstanten mit dem Suffix "_SIZE" anstelle von "_LEN" enthalten Speicherplatz für die Beendigung `null`.

|Konstante|Wert|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
