---
title: SccGetCommandOptions-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9685d96c14f3519653025ab1554f1e9e7587e0b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434644"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions-Funktion
Diese Funktion wird der Benutzer für die erweiterten Optionen für einen bestimmten Befehl aufgefordert.

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

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 iCommand

[in] Der Befehl für die erweiterte Optionen angefordert werden (finden Sie unter [Befehl Code](../extensibility/command-code-enumerator.md) mögliche Werte).

 ppvOptions

[in] Die Option-Struktur (kann auch sein, `NULL`).

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Erfolgreich.|
|SCC_I_ADV_SUPPORT|Das Quellcodeverwaltungs-Plug-in unterstützt erweiterte Optionen für den Befehl.|
|SCC_I_OPERATIONCANCELED|Der Benutzer abgebrochen wird, die Datenquellen-Steuerelement-Plug-ins **Optionen** Dialogfeld.|
|SCC_E_OPTNOTSUPPORTED|Das Quellcodeverwaltungs-Plug-in wird dieser Vorgang nicht unterstützt.|
|SCC_E_ISCHECKEDOUT|Dieser Vorgang für eine Datei, die, die derzeit ausgecheckt ist, kann nicht ausgeführt werden.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Die IDE ruft diese Funktion zum ersten Mal mit `ppvOptions` = `NULL` zu bestimmen, ob das Quellcodeverwaltungs-Plug-in das Feature der erweiterten Optionen für den angegebenen Befehl unterstützt. Wenn das plug-in das Feature für diesen Befehl unterstützt wird, die IDE ruft diese Funktion erneut aus, wenn der Benutzer die erweiterte Optionen anfordert (wie in der Regel implementiert ein **erweitert** Schaltfläche in einem Dialogfeld) und liefert einen nicht-NULL-Zeiger für `ppvOptions` , verweist auf eine `NULL` Zeiger. Das plug-in speichert alle erweiterten Optionen, die vom Benutzer in einer privaten Struktur angegeben und gibt einen Zeiger auf dieser Struktur in `ppvOptions`. Diese Struktur wird dann an alle anderen Source Control-Plug-in-API-Funktionen, die kennen, einschließlich der nachfolgende Aufrufe müssen übergeben die `SccGetCommandOptions` Funktion.

 Ein Beispiel kann hilfreich sein, diese Situation zu ermitteln.

 Wählt ein Benutzer die **abrufen** Befehl und die IDE zeigt eine **abrufen** Dialogfeld. Die IDE-Aufrufe der `SccGetCommandOptions` Funktion `iCommand` festgelegt `SCC_COMMAND_GET` und `ppvOptions` festgelegt `NULL`. Dies wird durch das Quellcodeverwaltungs-Plug-in als Frage interpretiert, "Haben Sie alle erweiterten Optionen für diesen Befehl?" Wenn das plug-in gibt `SCC_I_ADV_SUPPORT`, zeigt die IDE eine **erweitert** Schaltfläche seine **erhalten** im Dialogfeld.

 Zum ersten Mal der Benutzer klickt die **erweitert** Schaltfläche die IDE erneut Aufrufen der `SccGetCommandOptions` ordnungsgemäß verwendet werden, dieses Mal mit einer nicht -`NULL``ppvOptions` , verweist auf eine `NULL` Zeiger. Das plug-in angezeigt eigene **Abrufoptionen** Dialogfeld fordert den Benutzer Informationen diese Information in ihre eigene Struktur, und gibt einen Zeiger auf dieser Struktur in `ppvOptions`.

 Wenn der Benutzer klickt **erweitert** im gleichen Dialogfeld, ruft die IDE erneut der `SccGetCommandOptions` Funktion erneut ohne `ppvOptions`, sodass die Struktur an das plug-in zurückgegeben wird. Dies ermöglicht das plug-in, das Dialogfeld mit den Werten erneut zu initialisieren, die der Benutzer zuvor festgelegt haben. Das plug-in wird vor der Rückgabe die Struktur an Ort geändert.

 Abschließend, wenn der Benutzer klickt **OK** in der IDE **erhalten** (Dialogfeld), die IDE-Aufrufe der [SccGet](../extensibility/sccget-function.md), übergeben die Struktur zurückgegeben `ppvOptions` , enthält die Erweiterte Optionen.

> [!NOTE]
> Der Befehl `SCC_COMMAND_OPTIONS` wird verwendet, wenn die IDE zeigt eine **Optionen** Dialogfeld, das der Benutzer kann Festlegen der Einstellungen, die steuern, wie die Integration funktioniert. Wenn möchte, dass das Quellcodeverwaltungs-Plug-in ein eigenes Dialogfeld Einstellungen angeben, können sie anzeigen, aus einer **erweitert** Schaltfläche im Dialogfeld "Einstellungen" der IDE. Das plug-in ist allein verantwortlich für das Abrufen und Speichern dieser Informationen. die IDE nicht verwenden, oder ändern Sie sie.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Befehlscode](../extensibility/command-code-enumerator.md)