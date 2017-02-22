---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program-Methode"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft das Programm Zeichenfolge ab, die verwendet wird, um den Registern Gruppe vor dem Aufruf der aktuellen Funktion abzuleiten.  
  
## Syntax  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt das Programm Zeichenfolge zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Zeichenfolge des Programms ist eine Sequenz von Makros, die interpretiert wird, um das Präfix zu erstellen.  Zum Beispiel könnte ein typischer Stapelrahmen das Programm `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`Zeichenfolge.  Das Format lautet klammerfreie Rückschreibweise, in der die Operatoren den Operanden entsprechen.  `T0` stellt eine temporäre Variable im Stapel dar.  Dieses Beispiel führt die folgenden Schritte aus:  
  
1.  Inhalt des Registers `ebp` zu verschieben `T0`.  
  
2.  Fügen Sie `4` dem Wert in `T0` hinzu, um eine Adresse zu erstellen, rufen Sie den Wert von dieser Adresse ab, und speichern Sie den Wert im `eip`registrieren.  
  
3.  Rufen Sie den Wert aus der Adresse ab, die in `T0` gespeichert wird und speichern Sie diesen Wert im Register `ebp`.  
  
4.  Fügen Sie `8` dem Wert in `T0` hinzufügen, und speichern Sie diesen Wert im Register `esp`.  
  
 Beachten Sie, dass die Zeichenfolge für den CPU\- und dem Programm setup Aufrufkonvention der Funktion bestimmt ist, die durch den aktuellen Stapelrahmen dargestellt wird.  
  
## Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)