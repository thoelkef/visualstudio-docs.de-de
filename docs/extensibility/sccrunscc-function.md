---
title: SccRunScc Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ad179325c4f34cd206a3c5e6b0840a69dd46037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccrunscc-function"></a>SccRunScc-Funktion
Das Verwaltungstool des Datenquellen-Steuerelement ruft diese Funktion.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array der Namen der ausgewählten Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Source Control-Verwaltungstool wurde erfolgreich aufgerufen.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC_E_INITIALIZEFAILED|Fehler beim Initialisieren der Quellcodeverwaltungssystem.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte.|  
|SCC_E_CONNECTIONFAILURE|Fehler beim Verbinden mit dem Quellcodeverwaltungssystem.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ermöglicht dem Aufrufer das gesamte Spektrum der Funktionen von dem Quellcodeverwaltungssystem über ein externes Verwaltungstool zugreifen. Wenn vom Quellcodeverwaltungssystem keine Benutzeroberfläche verfügt, kann die Datenquellen-Steuerelement-Plug-in eine Schnittstelle zum Ausführen der erforderlichen Administrationsfunktionen implementieren.  
  
 Diese Funktion wird mit einer Anzahl und ein Array von Dateinamen für die aktuell ausgewählten Dateien aufgerufen. Wenn das Verwaltungstool unterstützt wird, kann die Liste der Dateien verwendet werden, um Dateien in der Verwaltungsschnittstelle vorab auswählen; Andernfalls kann die Liste ignoriert werden.  
  
 Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer wählt die **starten \<Quellcodeverwaltungsserver >** aus der **Datei** -> **Quellcodeverwaltung** Menü ". Dies **starten** Menüoption immer deaktiviert, oder auch durch Festlegen eines Registrierungseintrags ausgeblendet werden kann. Finden Sie unter [Vorgehensweise: Installieren Sie eine Datenquellen-Steuerelement-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md) für Details. Diese Funktion wird aufgerufen, wenn nur [SccInitialize](../extensibility/sccinitialize-function.md) gibt die `SCC_CAP_RUNSCC` Funktion Bit (finden Sie unter [Capability Flags](../extensibility/capability-flags.md) ausführliche Informationen zu dieser und anderen Funktionsbits).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Vorgehensweise: Installieren Sie ein Quellcodeverwaltungs-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Capability-Flags](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)