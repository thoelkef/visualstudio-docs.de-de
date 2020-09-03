---
title: Getautoinsertextensions-Methode
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543506"
---
# <a name="getautoinsertextensions-method"></a>Getautoinsertextensions-Methode
  Ruft Informationen zu den Apps für Office ab, die während des Debuggens automatisch eingefügt werden sollen.

 Diese Methode ist für eine spätere Verwendung vorgesehen.

## <a name="syntax"></a>Syntax

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*psaextensionnames*|Die Erweiterungs Namen der Apps für Office.|

## <a name="return-value"></a>Rückgabewert
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.

## <a name="remarks"></a>Bemerkungen
 Jede APP für Office, die eingefügt werden soll, wird als Name der Office-Anwendungs Erweiterung zurückgegeben, was einem Wert unter **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**entspricht. Der Host muss diese Werte in der Registrierung suchen und die Erweiterungen dann automatisch einfügen.
