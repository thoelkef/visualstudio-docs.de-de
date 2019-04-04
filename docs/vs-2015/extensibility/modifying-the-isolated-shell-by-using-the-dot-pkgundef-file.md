---
title: Ändern der Isolated Shell mithilfe der. Pkgundef-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961943"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Ändern der Isolated Shell mithilfe der. Pkgundef-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die pkgundef-Datei zum Ausschließen von angegebenen Registrierungseinträge in einer isolierten Shell-Anwendung ändern. In der Regel kopiert beim ersten, die eine Anwendung auf einem Computer gestartet wird die Visual Studio-Shell die vorhandene Visual Studio-Registrierungseinträge in den Stamm-Registrierungsschlüssel für die Anwendung. Dies schließt alle Verweise, die derzeit installierten VSPackages.  
  
 Fügen Sie zum Ausschließen eines bestimmten Registrierungseintrags in einer isolierten Shell-Anwendung in die Anwendung-pkgundef-Datei gefolgt von der Paket-Schlüssel durch den Eintrag. Schlüssel und Einträge werden genau wie in der PKGDEF-Datei dargestellt. d. h. als [$RootKey$] oder [$RootKey$\\*Unterschlüssel*] und "*Eintrag*" =*Wert*, wobei *Unterschlüssel* der Unterschlüssel beeinflussen, *Eintrag* ist der Eintrag zu entfernen, und *Wert* ist entweder `""` oder `dword:00000000`.  
  
 Um mehrere Einträge aus einem Registrierungsschlüssel auszuschließen, sondern nur Auflisten des Schlüssels einmal, gefolgt von einer Zeile für jeden Eintrag ausschließen.  
  
 Um einen Registrierungsschlüssel für die gesamte von einer isolierten Shell-Anwendung zu auszuschließen, fügen Sie den Schlüssel in die Anwendung pkgundef-Datei, aber geben Sie keinen keine Registrierungseinträge für diesen Schlüssel an.  
  
 Sie können der pkgundef-Datei Kommentare hinzufügen. Ein einzeiliger Kommentar muss zwei Schrägstriche als die ersten beiden Zeichen aufweisen.  
  
 So entfernen Sie beispielsweise die **Herstellen einer Verbindung mit Datenbank** und **Herstellen einer Verbindung mit Server-R** von Befehlen auf die **Tools** im Menü können Sie die auskommentierung die Zeile aufheben:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 ein, und fügen Sie die Zeile:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 in der Anwendung pkgundef-Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)   
 [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md)
