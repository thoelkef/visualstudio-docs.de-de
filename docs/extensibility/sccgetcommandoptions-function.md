---
title: SccGetCommandOptions-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700833"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions-Funktion
Diese Funktion fordert den Benutzer zur Eingabe erweiterter Optionen für einen bestimmten Befehl auf.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 Icommand

[in] Der Befehl, für den erweiterte Optionen angefordert werden (siehe [Befehlscode](../extensibility/command-code-enumerator.md) für mögliche Werte).

 ppvOptionen

[in] Die Optionsstruktur (kann `NULL`auch sein ).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg.|
|SCC_I_ADV_SUPPORT|Das Quellcodeverwaltungs-Plug-In unterstützt erweiterte Optionen für den Befehl.|
|SCC_I_OPERATIONCANCELED|Der Benutzer hat das Dialogfeld **Optionen** des Quellcodeverwaltungs-Plug-Ins abgebrochen.|
|SCC_E_OPTNOTSUPPORTED|Das Quellcodeverwaltungs-Plug-In unterstützt diesen Vorgang nicht.|
|SCC_E_ISCHECKEDOUT|Dieser Vorgang kann für eine aktuell ausgecheckte Datei nicht ausgeführt werden.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion `ppvOptions` = `NULL` zum ersten Mal auf, um festzustellen, ob das Quellcodeverwaltungs-Plug-In die erweiterte Optionsfunktion für den angegebenen Befehl unterstützt. Wenn das Plug-In die Funktion für diesen Befehl unterstützt, ruft die IDE diese Funktion **Advanced** erneut auf, wenn der Benutzer erweiterte Optionen `ppvOptions` anfordert (in der Regel als erweiterte Schaltfläche in einem Dialogfeld implementiert) und einen Nicht-NULL-Zeiger dafür bereitstellt, der auf einen `NULL` Zeiger zeigt. Das Plug-In speichert alle erweiterten Optionen, die vom Benutzer in einer `ppvOptions`privaten Struktur angegeben wurden, und gibt einen Zeiger auf diese Struktur in zurück. Diese Struktur wird dann an alle anderen Quellcodeverwaltungs-Plug-In-API-Funktionen übergeben, `SccGetCommandOptions` die darüber Bescheid wissen müssen, einschließlich nachfolgender Aufrufe der Funktion.

 Ein Beispiel kann helfen, diese Situation zu klären.

 Ein Benutzer wählt den Befehl **Abrufen** aus, und die IDE zeigt ein **Dialogfeld Abrufen** an. Die IDE `SccGetCommandOptions` ruft `iCommand` die `SCC_COMMAND_GET` Funktion `ppvOptions` auf `NULL`und setzt auf . Dies wird vom Quellcodeverwaltungs-Plug-In als die Frage interpretiert: "Haben Sie erweiterte Optionen für diesen Befehl?" Wenn das Plug-In zurückgegeben wird, `SCC_I_ADV_SUPPORT`zeigt die IDE im Dialogfeld **Abrufen** eine Schaltfläche **"Erweitert"** an.

 Wenn der Benutzer zum **Advanced** ersten Mal auf die `SccGetCommandOptions` Schaltfläche Erweitert klickt,`NULL``ppvOptions` ruft die `NULL` IDE die Funktion erneut auf, diesmal mit einem Nicht-Zeiger, der auf einen Zeiger zeigt. Das Plug-In zeigt sein eigenes Dialogfeld **Optionen abrufen** an, fordert den Benutzer zur Eingabe von Informationen `ppvOptions`auf, fügt diese Informationen in eine eigene Struktur ein und gibt einen Zeiger auf diese Struktur in zurück.

 Wenn der Benutzer **Advanced** im selben Dialogfeld erneut auf `SccGetCommandOptions` Erweitert klickt, ruft die IDE die Funktion erneut auf, ohne zu ändern, `ppvOptions`sodass die Struktur an das Plug-In zurückübergaben wird. Dadurch kann das Plug-In sein Dialogfeld erneut auf die Werte initialisieren, die der Benutzer zuvor festgelegt hatte. Das Plug-In ändert die Struktur vor der Rückgabe.

 Wenn der Benutzer im Dialogfeld **Abrufen** der IDE auf **OK** klickt, ruft die IDE `ppvOptions` [sccGet](../extensibility/sccget-function.md)auf, indem die zurückgegebene Struktur die erweiterten Optionen übergibt.

> [!NOTE]
> Der `SCC_COMMAND_OPTIONS` Befehl wird verwendet, wenn die IDE ein Dialogfeld **Optionen** anzeigt, in dem der Benutzer Einstellungen festlegen kann, die steuern, wie die Integration funktioniert. Wenn das Quellcodeverwaltungs-Plug-In sein eigenes Einstellungsdialogfeld bereitstellen möchte, kann es es über eine **Erweiterte** Schaltfläche im Dialogfeld "Einstellungen der IDE" anzeigen. Das Plug-in ist allein für das Abrufen und Beharren dieser Informationen verantwortlich; die IDE verwendet sie nicht oder ändert sie nicht.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Befehlscode](../extensibility/command-code-enumerator.md)
