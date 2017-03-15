---
title: "Ändern die isolierte Shell mithilfe der. Pkgundef Datei | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Ändern die isolierte Shell mithilfe der. Pkgundef-Datei
Sie können die .pkgundef-Datei, um eine isolierte Shell-Anwendung angegebenen Registrierungseinträge ausgeschlossen ändern. In der Regel kopiert eine Anwendung auf einem Computer gestartet wird zum ersten Mal die Visual Studio-Shell die vorhandene Visual Studio-Registrierungseinträge in der Root-Registrierungsschlüssel für die Anwendung. Dies schließt alle Verweise, die aktuell installierte VSPackages.  
  
 Um einen bestimmten Registrierungseintrag aus einer Anwendung für isolierte Shells auszuschließen, gefolgt von der Paket-Schlüssel durch den Eintrag, für die Anwendung .pkgundef hinzufügen. Schlüssel und Einträge werden ebenso wie in der PKGDEF-Datei dargestellt. d. h. als [$RootKey$] oder [$RootKey$\\*Unterschlüssel*] und "*Eintrag*" =*Wert*, wobei *Unterschlüssel* der Unterschlüssel zu beeinflussen, *Eintrag* ist der Eintrag entfernt, und *Wert* ist entweder `""` oder `dword:00000000`.  
  
 Zum Ausschließen von Liste mehrere Einträge aus einem Registrierungsschlüssel, der nur den Schlüssel einmalig, gefolgt von einer Zeile für jeden Eintrag ausschließen.  
  
 Um eine gesamte Registrierungsschlüssel aus einer Anwendung isolierte Shell auszuschließen, fügen Sie den Schlüssel für die Anwendung .pkgundef, jedoch Geben Sie keine Registrierungseinträge für diesen Schlüssel nicht an.  
  
 Sie können Kommentare in die Datei .pkgundef hinzufügen. Ein einzeiliger Kommentar muss zwei Schrägstriche als die ersten beiden Zeichen aufweisen.  
  
 Z. B. Entfernen der **mit Datenbank verbinden** und **mit dienen r** Befehle auf der **Tools** Menü können Sie kommentieren Sie die Zeile:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 und fügen Sie die Zeile:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 .pkgundef-Datei der Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Paket-GUIDs der Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)   
 [Anpassen der isolierte Shells](../extensibility/customizing-the-isolated-shell.md)
