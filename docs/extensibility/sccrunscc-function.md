---
title: "SccRunScc-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc-Funktion"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRunScc-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft das Datenquellen\-Steuerelement\-Verwaltungstool.  
  
## Syntax  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Ein Array der ausgewählten Dateinamen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Das Datenquellen\-Steuerelement\-Verwaltungstool wurde erfolgreich aufgerufen.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|  
|SCC\_E\_INITIALIZEFAILED|Fehler beim Initialisieren des Quellcode\-Verwaltungssystem.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte.|  
|SCC\_E\_CONNECTIONFAILURE|Fehler beim Verbinden mit dem Quellcodeverwaltungssystem.|  
|SCC\_E\_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht in einem Quellcodeverwaltungsprojekt.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Diese Funktion ermöglicht den Aufrufer, den vollen Umfang der Features von Quellcode\-Verwaltungssystem über ein externes Verwaltungstool zugreifen. Wenn Quellcode\-Verwaltungssystem keine Benutzeroberfläche besitzt, kann das Quellcodeverwaltungs\-Plug\-in eine Schnittstelle zum Ausführen der erforderlichen Funktionen implementieren.  
  
 Diese Funktion ist mit einem Zähler und ein Array von Dateinamen für die ausgewählten Dateien aufgerufen. Wenn das Verwaltungstool unterstützt wird, kann die Liste der Dateien verwendet werden, auf die Dateien in die Verwaltungsoberfläche vorab auswählen. Andernfalls kann die Liste ignoriert werden.  
  
 Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer wählt die **Launch \< Quellcodeverwaltungsserver \>** aus der **Datei** \-\> **Source Control** Menü. Diese **Starten** Menüoption immer deaktiviert oder sogar durch Festlegen eines Registrierungseintrags ausgeblendet werden kann. Ausführliche Informationen finden Sie unter [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md). Diese Funktion wird nur aufgerufen, wenn [SccInitialize](../extensibility/sccinitialize-function.md) Gibt die `SCC_CAP_RUNSCC` Funktion Bit \(finden Sie unter [Capability Flags](../extensibility/capability-flags.md) ausführliche Informationen über diese und andere Funktionen\).  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Gewusst wie: Installieren Sie ein Quellcodeverwaltungs\-Plug\-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Capability Flags](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)