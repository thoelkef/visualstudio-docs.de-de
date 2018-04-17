---
title: SccGetCommandOptions Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60245b7fab3c2a0b313ccbe1d7393b0783962a37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions-Funktion
Diese Funktion fordert den Benutzer für die erweiterten Optionen für einen bestimmten Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 iCommand  
 [in] Der Befehl für die erweiterte Optionen angefordert werden (finden Sie unter [Befehlscode](../extensibility/command-code-enumerator.md) mögliche Werte).  
  
 ppvOptions  
 [in] Die Option-Struktur (kann auch `NULL`).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolgreich.|  
|SCC_I_ADV_SUPPORT|Die Datenquellen-Steuerelement-Plug-in unterstützt erweiterte Optionen für den Befehl.|  
|SCC_I_OPERATIONCANCELED|Die Datenquellen-Steuerelement-Plug-ins vom Benutzer abgebrochen. **Optionen** (Dialogfeld).|  
|SCC_E_OPTNOTSUPPORTED|Dieser Vorgang wird von der quellcodeverwaltung-Plug-in nicht unterstützt.|  
|SCC_E_ISCHECKEDOUT|Dieser Vorgang auf eine Datei, die zurzeit ausgecheckt ist, kann nicht ausgeführt werden.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE ruft diese Funktion zum ersten Mal mit `ppvOptions` = `NULL` zu bestimmen, ob die Datenquellen-Steuerelement-Plug-in die Funktion erweiterte Optionen für den angegebenen Befehl unterstützt. Wenn das plug-in die Funktion für diesen Befehl unterstützt, die IDE ruft diese Funktion erneut, wenn der Benutzer die erweiterte Optionen anfordert (implementiert in der Regel als ein **erweitert** Schaltfläche in einem Dialogfeld) und liefert einen nicht-NULL-Zeiger für `ppvOptions` , verweist auf eine `NULL` Zeiger. Das plug-in speichert alle erweiterten Optionen, die vom Benutzer in einer privaten Struktur angegeben und gibt einen Zeiger auf dieser Struktur in `ppvOptions`. Diese Struktur wird dann an andere Datenquellen-Steuerelement-Plug-in-API-Funktionen, die erfahren einschließlich nachfolgende Aufrufe müssen übergeben der `SccGetCommandOptions` Funktion.  
  
 Ein Beispiel kann Ihnen helfen, diese Situation zu ermitteln.  
  
 Ein Benutzer wählt die **abrufen** Befehl und der IDE angezeigt ein **abrufen** (Dialogfeld). Ruft die IDE die `SccGetCommandOptions` funktionieren mit `iCommand` festgelegt `SCC_COMMAND_GET` und `ppvOptions` festgelegt `NULL`. Dies wird durch die quellcodeverwaltung-Plug-in als Frage interpretiert, "Haben Sie erweiterte Optionen für diesen Befehl?" Wenn das plug-in zurückgibt `SCC_I_ADV_SUPPORT`, zeigt die IDE eine **erweitert** Schaltfläche seine **abrufen** (Dialogfeld).  
  
 Der Benutzer klickt erstmalig den **erweitert** Schaltfläche die IDE erneut aufgerufen der `SccGetCommandOptions` funktionieren, dieses Mal mit einem nicht-`NULL``ppvOptions` , verweist auf eine `NULL` Zeiger. -Plug-in zeigt einen eigenen **Abrufoptionen** Dialogfeld fordert den Benutzer Informationen diese Information in ihre eigene Struktur und gibt einen Zeiger auf dieser Struktur in `ppvOptions`.  
  
 Wenn der Benutzer klickt **erweitert** im gleichen Dialogfeld, ruft die IDE erneut die `SccGetCommandOptions` Funktion erneut, ohne Änderung `ppvOptions`, sodass die Struktur für das angegebene plug-in übergeben wird. Dies ermöglicht das plug-in, das ein Dialogfeld mit den Werten, die der Benutzer zuvor festgelegt wurden, erneut zu initialisieren. Das plug-in ändert die Struktur an Ort vor der Rückgabe.  
  
 Abschließend, wenn der Benutzer klickt **OK** in der IDE **abrufen** (Dialogfeld), ruft die IDE die [SccGet](../extensibility/sccget-function.md), übergeben die Struktur zurückgegeben `ppvOptions` , enthält die Erweiterte Optionen.  
  
> [!NOTE]
>  Der Befehl `SCC_COMMAND_OPTIONS` wird verwendet, wenn die IDE zeigt eine **Optionen** (Dialogfeld), die der Benutzer kann Voreinstellungen, die steuern, wie die Integration funktioniert. Möchte, dass die Datenquellen-Steuerelement-Plug-in ein eigenes Dialogfeld Einstellungen angeben, zeigt es aus einem **erweitert** Schaltfläche im Dialogfeld "Einstellungen" der IDE. Das plug-in ist allein verantwortlich für das Abrufen und diese Informationen beibehalten. die IDE verwenden, oder ändern Sie sie nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Befehls-Code](../extensibility/command-code-enumerator.md)