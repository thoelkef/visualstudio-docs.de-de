---
title: "SccGetCommandOptions-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetCommandOptions"
helpviewer_keywords: 
  - "SccGetCommandOptions-Funktion"
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccGetCommandOptions-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion fordert den Benutzer um weitere Optionen für einen bestimmten Befehl.  
  
## Syntax  
  
```cpp#  
SCCRTN SccGetCommandOptions(  
   LPVOID pvContext,  
   HWND hWnd,  
   enum SCCCOMMAND iCommand,  
   LPCMDOPTS* ppvOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 iCommand  
 \[in\] Der Befehl für die erweiterte Optionen angefordert werden \(siehe [Befehlscode](../extensibility/command-code-enumerator.md) Mögliche Werte\).  
  
 ppvOptions  
 \[in\] Die Option\-Struktur \(kann auch `NULL`\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Erfolgreich.|  
|SCC\_I\_ADV\_SUPPORT|Das Quellcodeverwaltungs\-Plug\-in unterstützt erweiterte Optionen für den Befehl.|  
|SCC\_I\_OPERATIONCANCELED|Die Datenquellen\-Steuerelement\-Plug\-ins vom Benutzer abgebrochen **Optionen** \(Dialogfeld\).|  
|SCC\_E\_OPTNOTSUPPORTED|Dieser Vorgang wird von das Datenquellen\-Steuerelement\-Plug\-in nicht unterstützt.|  
|SCC\_E\_ISCHECKEDOUT|Dieser Vorgang für eine Datei ist nicht möglich, die derzeit ausgecheckt ist.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Die IDE ruft diese Funktion zum ersten Mal mit `ppvOptions`\=`NULL` bestimmt, ob das Datenquellen\-Steuerelement, das Plug\-in\-Funktion für die erweiterten Optionen für den angegebenen Befehl unterstützt. Wenn das plug\-in die Funktion für diesen Befehl nicht unterstützt, die IDE ruft diese Funktion erneut, wenn der Benutzer die erweiterte Optionen anfordert \(wie in der Regel implementiert ein **Erweitert** Schaltfläche in einem Dialogfeld\) und liefert einen nicht\-NULL\-Zeiger für `ppvOptions` verweist auf eine `NULL` Zeiger. Das plug\-in speichert die vom Benutzer in einer private\-Struktur angegebenen Optionen und gibt einen Zeiger auf diese Struktur in `ppvOptions`. Diese Struktur wird dann an andere Source Control\-Plug\-in API\-Funktionen, die kennen, einschließlich nachfolgende Aufrufe übergeben der `SccGetCommandOptions` Funktion.  
  
 Ein Beispiel können Sie diese Situation zu ermitteln.  
  
 Ein Benutzer die **abrufen** Befehl und der IDE angezeigt ein **abrufen** \(Dialogfeld\). Die IDE\-Aufrufe der `SccGetCommandOptions` \-Funktion mit `iCommand` festgelegt `SCC_COMMAND_GET` und `ppvOptions` festgelegt `NULL`. Dies wird durch das Quellcodeverwaltungs\-Plug\-in als Frage interpretiert, "Haben Sie erweiterte Optionen für diesen Befehl?" Wenn das plug\-in gibt `SCC_I_ADV_SUPPORT`, zeigt die IDE eine **Erweitert** Schaltfläche seine **abrufen** \(Dialogfeld\).  
  
 Beim ersten Klick auf die **Erweitert** Schaltfläche die IDE erneut Aufrufen der `SccGetCommandOptions` funktionieren, dieses Mal mit einem nicht\-`NULL` `ppvOptions` verweist auf eine `NULL` Zeiger.  Das plug\-in angezeigt eigene **Abrufoptionen** fordert den Benutzer Informationen im Dialogfeld diese Information in ihre eigene Struktur und gibt einen Zeiger auf diese Struktur in `ppvOptions`.  
  
 Klickt der Benutzer **Erweitert** im gleichen Dialogfeld Ruft die IDE erneut die `SccGetCommandOptions` Funktion erneut ohne `ppvOptions`, sodass die Struktur auf das plug\-in übergeben wird. Dies ermöglicht das plug\-in, das Dialogfeld, um die Werte erneut zu initialisieren, die der Benutzer zuvor festgelegt haben. Das plug\-in wird vor der Rückgabe die Struktur an Ort geändert.  
  
 Abschließend klickt der Benutzer **OK** in der IDE **abrufen** \(Dialogfeld\), die IDE\-Aufrufe der [SccGet](../extensibility/sccget-function.md), und übergeben Sie die Struktur zurückgegeben `ppvOptions` die die erweiterten Optionen enthält.  
  
> [!NOTE]
>  Mit dem Befehl `SCC_COMMAND_OPTIONS` wird verwendet, wenn die IDE zeigt eine **Optionen** \(Dialogfeld\), die der Benutzer Voreinstellungen, die steuern, wie die Integration funktioniert. Möchte, dass das Quellcodeverwaltungs\-Plug\-in ein eigenes Dialogfeld Voreinstellungen angeben, zeigt es aus einer **Erweitert** Schaltfläche in der IDE\-Dialogfelds. Das plug\-in ist allein verantwortlich für das Abrufen und diese Informationen beibehalten. die IDE nicht verwenden, oder ändern Sie sie.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Befehlscode](../extensibility/command-code-enumerator.md)