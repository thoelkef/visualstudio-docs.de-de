---
title: SccSetOption-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700309"
---
# <a name="sccsetoption-function"></a>SccSetOption-Funktion
Diese Funktion legt Optionen fest, die das Verhalten des Quellcodeverwaltungs-Plug-Ins steuern.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 nOption

[in] Die Option, die festgelegt wird.

 dwVal

[in] Einstellungen für die Option.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Option wurde erfolgreich festgelegt.|
|SCC_I_SHARESUBPROJOK|Wird `nOption` zurückgegeben, wenn es war, `SCC_OPT_SHARESUBPROJ` und das Quellcodeverwaltungs-Plug-In ermöglicht es der IDE, den Zielordner festzulegen.|
|SCC_E_OPNOTSUPPORTED|Die Option wurde nicht festgelegt und sollte nicht in Anspruch genommen werden.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion auf, um das Verhalten des Quellcodeverwaltungs-Plug-Ins zu steuern. Der erste `nOption`Parameter , , gibt den Wert an, der festgelegt wird, während der zweite, , angibt, `dwVal`was mit diesem Wert zu tun ist. Das Plug-In speichert diese `pvContext``,` Informationen, die einem zugeordnet sind, sodass die IDE diese Funktion aufrufen muss, nachdem sie [SccInitialize](../extensibility/sccinitialize-function.md) aufgerufen hat (aber nicht unbedingt nach jedem Aufruf des [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Zusammenfassung der Optionen und ihrer Werte:

|`nOption`|`dwValue`|BESCHREIBUNG|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Aktiviert/deaktiviert die Warteschlange von Hintergrundereignis.|
|`SCC_OPT_USERDATA`|Willkürlicher Wert|Gibt einen Benutzerwert an, der an die [OptNAMECHANGEPFN-Rückruffunktion](../extensibility/optnamechangepfn.md) übergeben werden soll.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Gibt an, ob die IDE derzeit das Abbrechen eines Vorgangs unterstützt.|
|`SCC_OPT_NAMECHANGEPFN`|Zeiger auf die [OPTNAMECHANGEPFN-Rückruffunktion](../extensibility/optnamechangepfn.md)|Legt einen Zeiger auf eine Rückruffunktion zur Namensänderung fest.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Gibt an, ob die IDE das manuelle Auschecken ihrer Dateien zulässt (über die Quellcodeverwaltungsbenutzeroberfläche) oder ob sie nur über das Quellcodeverwaltungs-Plug-In ausgecheckt werden müssen.|
|`SCC_OPT_SHARESUBPROJ`|Nicht zutreffend|Wenn das Quellcodeverwaltungs-Plug-In der IDE erlaubt, den lokalen `SCC_I_SHARESUBPROJOK`Projektordner anzugeben, gibt das Plug-In zurück.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Falls `nOption` `SCC_OPT_EVENTQUEUE`dies der Fall ist, deaktiviert die IDE die Hintergrundverarbeitung (oder aktiviert sie erneut). Beispielsweise weist die IDE während einer Kompilierung das Quellcodeverwaltungs-Plug-In an, die Verarbeitung im Leerlauf jeglicher Art zu beenden. Nach der Kompilierung wird die Hintergrundverarbeitung wieder aktiviert, um die Ereigniswarteschlange des Plug-Ins auf dem neuesten Stand zu halten. Entsprechend dem `SCC_OPT_EVENTQUEUE` Wert `nOption`von gibt es `dwVal`zwei mögliche `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE`Werte für , nämlich, und .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Wenn der `nOption` Wert `SCC_OPT_HASCANCELMODE`für ist , ermöglicht die IDE Benutzern, lange Vorgänge abzubrechen. Die `dwVal` `SCC_OPT_HCM_NO` Einstellung auf (Standardeinstellung) gibt an, dass die IDE keinen Abbruchmodus hat. Das Quellcodeverwaltungs-Plug-In muss eine eigene Schaltfläche Abbrechen anbieten, wenn der Benutzer abbrechen kann. `SCC_OPT_HCM_YES`gibt an, dass die IDE die Möglichkeit bietet, einen Vorgang abzubrechen, sodass das SCC-Plug-In keine eigene Schaltfläche Abbrechen anzeigen muss. Wenn die `dwVal` IDE `SCC_OPT_HCM_YES`auf festgelegt ist, `SCC_MSG_STATUS` `DOCANCEL` ist sie `lpTextOutProc` bereit, auf die Rückruffunktion zu reagieren und Nachrichten an die Rückruffunktion zu senden (siehe [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Wenn die IDE diese Variable nicht setzt, sollte das Plug-In diese beiden Nachrichten nicht senden.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Wenn nOption auf `SCC_OPT_NAMECHANGEPFN`gesetzt ist und sowohl das Quellcodeverwaltungs-Plug-In als auch die IDE dies zulassen, kann das Plug-In eine Datei während eines Quellcodeverwaltungsvorgangs umbenennen oder verschieben. Der `dwVal` wird auf einen Funktionszeiger vom Typ [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)gesetzt. Während eines Quellcodeverwaltungsvorgangs kann das Plug-In diese Funktion aufrufen und drei Parameter übergeben. Dies sind der alte Name (mit vollqualifiziertem Pfad) einer Datei, der neue Name (mit vollqualifiziertem Pfad) dieser Datei und ein Zeiger auf Informationen, die für die IDE relevant sind. Die IDE sendet diesen letzten `SccSetOption` Zeiger, `SCC_OPT_USERDATA`indem `dwVal` sie mit `nOption` satz auf auf anruft und auf die Daten zeigt. Die Unterstützung für diese Funktion ist optional. Ein VSSCI-Plug, der diese Fähigkeit verwendet, muss seine `NULL`Funktionszeiger- und Benutzerdatenvariablen auf initialisieren, und er darf keine Umbenennungsfunktion aufrufen, es sei denn, ihm wurde eine option gegeben. Sie sollte auch bereit sein, den ihm gegebenen Wert zu behalten `SccSetOption`oder ihn als Reaktion auf einen neuen Aufruf von zu ändern. Dies geschieht nicht in der Mitte eines Quellcodeverwaltungsbefehlsvorgangs, aber es kann zwischen Befehlen passieren.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Wenn nOption auf `SCC_OPT_SCCCHECKOUTONLY`gesetzt ist, gibt die IDE an, dass die Dateien im aktuell geöffneten Projekt niemals manuell über die Benutzeroberfläche des Quellcodeverwaltungssystems ausgecheckt werden sollten. Stattdessen sollten die Dateien nur über das Quellcodeverwaltungs-Plug-In unter IDE-Steuerung ausgecheckt werden. Wenn `dwValue` auf `SCC_OPT_SCO_NO`gesetzt ist, bedeutet dies, dass die Dateien vom Plug-In normal behandelt werden sollten und über die Quellcodeverwaltungsbenutzeroberfläche ausgecheckt werden können. Wenn `dwValue` auf `SCC_OPT_SCO_YES`festgelegt ist, darf nur das Plug-In Dateien auschecken, und die Benutzeroberfläche des Quellcodeverwaltungssystems sollte nicht aufgerufen werden. Dies ist für Situationen, in denen die IDE "Pseudo-Dateien" haben könnte, die sinnvoll sind, nur über die IDE auszuchecken.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Wenn`nOption` auf `SCC_OPT_SHARESUBPROJ`festgelegt ist, testet die IDE, ob das Quellcodeverwaltungs-Plug-In beim Hinzufügen von Dateien aus der Quellcodeverwaltung einen angegebenen lokalen Ordner verwenden kann. Der Wert `dwVal` des Parameters spielt in diesem Fall keine Rolle. Wenn das Plug-In der IDE erlaubt, den lokalen Zielordner anzugeben, in dem die Dateien aus der Quellcodeverwaltung hinzugefügt `SCC_I_SHARESUBPROJOK` werden, wenn [SccAddFromScc](../extensibility/sccaddfromscc-function.md) aufgerufen wird, muss das Plug-In zurückgegeben werden, wenn die `SccSetOption` Funktion aufgerufen wird. Die IDE verwendet `lplpFileNames` dann `SccAddFromScc` den Parameter der Funktion, um im Zielordner zu übergeben. Das Plug-In verwendet diesen Zielordner, um die aus der Quellcodeverwaltung hinzugefügten Dateien zu platzieren. Wenn das Plug-In `SCC_I_SHARESUBPROJOK` nicht `SCC_OPT_SHARESUBPROJ` zurückgegeben wird, wenn die Option festgelegt ist, geht die IDE davon aus, dass das Plug-In Dateien nur im aktuellen lokalen Ordner hinzufügen kann.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
