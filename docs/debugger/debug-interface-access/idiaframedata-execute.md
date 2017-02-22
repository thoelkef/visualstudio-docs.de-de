---
title: "IDiaFrameData::execute | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData::execute-Methode"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Führt Stapelentladung aus und gibt die Ergebnisse in einer Stackwalk Skinframes Oberfläche zurück.  
  
## Syntax  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Parameter  
 `frame`  
 \[in\]  Ein [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)\-Objekt, das den Zustand von Frames enthält, registriert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden die möglichen Rückgabewerte für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_DIA\_INPROLOG|Kann einen Stapelrahmen nicht als vorläufige im Code ausführen.|  
|E\_DIA\_SYNTAX|Analysefehler aufgetreten im Rahmen programm.|  
|E\_DIA\_FRAME\_ACCESS|Die Speicher oder Register verfügt.|  
|E\_DIA\_VALUE|Fehler bei der Berechnung eines Werts \(z. B. Division durch 0\).|  
  
## Hinweise  
 Diese Methode wird während des Debuggens aufgerufen, um den Stapel entladen.  Das [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)\-Objekt wird von der Clientanwendung Aktualisierungen von Registern zu empfangen und Methoden bereitzustellen `execute` implementiert, die von der Methode verwendet werden.  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)