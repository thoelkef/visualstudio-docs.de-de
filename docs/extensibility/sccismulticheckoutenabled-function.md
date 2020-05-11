---
title: SccIsMultiCheckoutEnabled-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700581"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled-Funktion
Diese Funktion prüft, ob das Quellcodeverwaltungs-Plug-In mehrere Auscheckungen für eine Datei zulässt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parameter
 pContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 pbMultiCheckout

[out] Gibt an, ob mehrere Auscheckungen für dieses Projekt aktiviert sind (ungleich Null bedeutet, dass mehrere Auscheckungen unterstützt werden).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Check war erfolgreich.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Die IDE führt zwei Prüfungen durch, um festzustellen, ob Dateien gleichzeitig von mehr als einem Benutzer ausgecheckt werden können. Zunächst muss das Quellcodeverwaltungssystem mehrere Auschecken unterstützen. Das Quellcodeverwaltungs-Plug-In kann diese Funktion während `SCC_CAP_MULTICHECKOUT`der Initialisierung angeben, indem es die . Danach ruft die IDE bei einer zweiten Prüfung diese Funktion auf, um festzustellen, ob das aktuelle Projekt mehrere Auscheckungen unterstützt. Wenn mehrere Auscheckvorgänge für das ausgewählte Projekt unterstützt werden, gibt `pbMultiCheckout` das Plug-In einen Erfolgscode zurück und setzt auf einen Wert ungleich Null (`TRUE`) oder `FALSE`.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
