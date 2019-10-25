---
title: Sccismulticheckoutenabled-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721079"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled-Funktion
Diese Funktion überprüft, ob das Quellcodeverwaltungs-Plug-in mehrere Auschecken für eine Datei zulässt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parameter
 pContext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 pbmulticheckout

vorgenommen Gibt an, ob mehrere Auschecken für dieses Projekt aktiviert sind (ungleich 0 (null) bedeutet, dass mehrere Auschecken unterstützt werden).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Überprüfung war erfolgreich.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Hinweise
 Die IDE führt zwei Überprüfungen durch, um zu bestimmen, ob Dateien gleichzeitig von mehr als einem Benutzer ausgecheckt werden können. Zuerst muss das Quell Code Verwaltungssystem mehrere Auscheck Vorgänge unterstützen. Das Quellcodeverwaltungs-Plug-in kann diese Funktion während der Initialisierung angeben, indem das `SCC_CAP_MULTICHECKOUT` angegeben wird. Danach ruft die IDE als zweite Überprüfung diese Funktion auf, um zu bestimmen, ob das aktuelle Projekt mehrere Auscheck Vorgänge unterstützt. Wenn mehrere Auscheck Vorgänge für das ausgewählte Projekt unterstützt werden, gibt das Plug-in einen Erfolgs Code zurück und legt `pbMultiCheckout` auf einen Wert ungleich 0 (`TRUE`) oder `FALSE` fest.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)