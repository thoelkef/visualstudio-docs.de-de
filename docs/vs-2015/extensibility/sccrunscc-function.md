---
title: SccRunScc-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdeaead9d4534188b7731e9add0bde6d56ad7e7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49242167"
---
# <a name="sccrunscc-function"></a>SccRunScc-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ruft das Datenquellen-Steuerelement-Verwaltungstool.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array der Namen der ausgewählten Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Datenquellen-Steuerelement-Verwaltungstool wurde erfolgreich aufgerufen.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC_E_INITIALIZEFAILED|Fehler beim Initialisieren der vom Quellcodeverwaltungssystem.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|  
|SCC_E_CONNECTIONFAILURE|Fehler bei der verbindungsherstellung auf das Quellcodeverwaltungssystem.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ermöglicht den Aufrufer, die das gesamte Spektrum an Funktionen des Quellcode-Verwaltungssystem über ein externes Verwaltungstool zugreifen. Wenn der Quellcode-Verwaltungssystems keine Benutzeroberfläche verfügt, kann das Quellcodeverwaltungs-Plug-in eine Schnittstelle zum Durchführen der erforderlichen Verwaltungsfunktionen implementieren.  
  
 Diese Funktion wird mit einem Zähler und ein Array von Dateinamen für die ausgewählten Dateien aufgerufen. Wenn das Verwaltungstool unterstützt wird, kann die Liste der Dateien auf die Vorauswahl von Dateien in der Verwaltungsschnittstelle verwendet werden. Andernfalls kann die Liste ignoriert werden.  
  
 Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer auswählt der **starten \<Quellcodeverwaltungsserver >** aus der **Datei** -> **Quellcodeverwaltung** ein Menü. Dies **starten** Menüoption immer deaktiviert oder sogar durch Festlegen eines Registrierungseintrags ausgeblendet werden kann. Finden Sie unter [Vorgehensweise: eine Source-Control-Plug-in installieren](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Details. Diese Funktion wird aufgerufen, wenn nur [SccInitialize](../extensibility/sccinitialize-function.md) gibt die `SCC_CAP_RUNSCC` Funktion Bit (finden Sie unter [Capability Flags](../extensibility/capability-flags.md) Weitere Informationen zu diesem und anderen Funktionsbits).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Funktionsflags](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

