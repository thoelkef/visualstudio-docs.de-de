---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: "Ändern von Isolated Shell mithilfe der. Pkgundef Datei | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4c0f46924c2c828158960a924faa031be0fd14
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Ändern von Isolated Shell mithilfe der. Pkgundef-Datei
Sie können die Datei .pkgundef zum Ausschließen der Einträge in der Registrierung angegebenen aus einer isolierten shellanwendung ändern. In der Regel kopiert eine Anwendung auf einem Computer gestartet wird zum ersten Mal die Visual Studio-Shell die vorhandenen Visual Studio-Registrierungseinträge in den Stamm-Registrierungsschlüssel für die Anwendung. Dies schließt alle Verweise auf die derzeit installierte VSPackages.  
  
 Fügen Sie zum Ausschließen eines bestimmten Registrierungseintrags in einer isolierten shellanwendung auf die Datei der Anwendung .pkgundef gefolgt von der Paket-Schlüssel durch den Eintrag hinzu. Schlüssel und Einträge werden wie in der PKGDEF-Datei dargestellt. d. h. als [$RootKey$] oder [$RootKey$\\*Unterschlüssel*] und "*Eintrag*" =*Wert*, wobei *Unterschlüssel* ist der Unterschlüssel, um zu beeinflussen, *Eintrag* ist der Eintrag zu entfernen, und *Wert* handelt es sich um `""` oder `dword:00000000`.  
  
 Um mehrere Einträge aus einem Registrierungsschlüssel auszuschließen, nur Liste des Schlüssels einmalig, gefolgt von einer Zeile für jeden Eintrag ausschließen.  
  
 Um eine gesamte Registrierungsschlüssel aus einer isolierten Shell-Anwendung auszuschließen, fügen Sie den Schlüssel in die Anwendung .pkgundef-Datei wird jedoch angegeben Sie keine Registrierungseinträge für diesen Schlüssel nicht.  
  
 Sie können Kommentare in die Datei .pkgundef hinzufügen. Ein einzeiliger Kommentar muss zwei Schrägstriche als die ersten beiden Zeichen aufweisen.  
  
 So entfernen Sie beispielsweise die **Verbindung mit Datenbank herstellen** und **Herstellen einer Verbindung mit Server-R** Befehle die **Tools** im Menü können Sie kommentieren Sie die Zeile:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 ein, und fügen Sie die Zeile:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 in der Anwendung .pkgundef-Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [Paket-GUIDs der Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)   
 [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md)