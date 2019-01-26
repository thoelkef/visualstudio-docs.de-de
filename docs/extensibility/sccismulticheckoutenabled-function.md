---
title: SccIsMultiCheckoutEnabled-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 883f67482881b40c9d685604e1ee30fa33d4048b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013508"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled-Funktion
Diese Funktion überprüft, ob das Quellcodeverwaltungs-Plug-in Mehrfaches Auschecken in einer Datei ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 pbMultiCheckout  
 [out] Gibt an, ob es sich bei Mehrfaches Auschecken für dieses Projekt (ungleich NULL bedeutet, dass Mehrfaches Auschecken unterstützt werden) aktiviert sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Überprüfung war erfolgreich.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE macht zwei prüft, ob Dateien von mehr als einem Benutzer ausgecheckt werden können. Zunächst muss das Quellcodeverwaltungssystem Mehrfaches Auschecken unterstützen. Das Quellcodeverwaltungs-Plug-in kann diese Funktion während der Initialisierung geben, indem Sie die `SCC_CAP_MULTICHECKOUT`. Danach, wie einer zweiten Überprüfung, ruft die IDE dieser Funktion können Sie bestimmen, ob das aktuelle Projekt Mehrfaches Auschecken unterstützt. Wenn Mehrfaches Auschecken für das ausgewählte Projekt unterstützt werden, die Plug-in-gibt ein Erfolg, code, und legt sie fest `pbMultiCheckout` zu ungleich Null (`TRUE`) oder `FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)