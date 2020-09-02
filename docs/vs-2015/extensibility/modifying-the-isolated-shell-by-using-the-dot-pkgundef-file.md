---
title: Ändern der isolierten Shell mithilfe von. Pkgundef-Datei | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538388"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Ändern der Isolated Shell mithilfe der PKGUNDEF-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die pkgundef-Datei so ändern, dass bestimmte Registrierungseinträge aus einer isolierten Shellanwendung ausgeschlossen werden. Wenn eine Anwendung zum ersten Mal auf einem Computer gestartet wird, kopiert Visual Studio Shell in der Regel die vorhandenen Visual Studio-Registrierungseinträge in den Stamm Registrierungsschlüssel für die Anwendung. Dies schließt alle Verweise auf zurzeit installierte VSPackages ein.  
  
 Um einen bestimmten Registrierungs Eintrag aus einer isolierten Shellanwendung auszuschließen, fügen Sie der Datei Application. pkgundef den Paket Schlüssel gefolgt vom Eintrag hinzu. Schlüssel und Einträge werden genau wie in der pkgdef-Datei dargestellt. Das heißt, wie [$RootKey $] oder [$RootKey $ \\ *unter Key*] und "*Entry*" =*value*, wobei *Unterschlüssel* der Unterschlüssel ist, der betroffen *entry* sein soll, ist der Eintrag der zu entfernende Eintrag, und der *Wert* ist entweder `""` oder `dword:00000000` .  
  
 Wenn Sie mehrere Einträge aus einem Registrierungsschlüssel ausschließen möchten, können Sie den Schlüssel nur einmal auflisten, gefolgt von einer Zeile für jeden auszuschließenden Eintrag.  
  
 Wenn Sie einen gesamten Registrierungsschlüssel aus einer isolierten Shellanwendung ausschließen möchten, fügen Sie den Schlüssel der Datei "Application. pkgundef" hinzu, aber geben Sie keine Registrierungseinträge für diesen Schlüssel an.  
  
 Sie können der pkgundef-Datei Kommentare hinzufügen. Ein einzeiligen Kommentar muss zwei Schrägstriche als die ersten beiden Zeichen aufweisen.  
  
 Wenn Sie z. b. die Befehle **Verbindung mit Datenbank herstellen** und **mit r verbinden** über **das Menü** Extras entfernen möchten, können Sie die Auskommentierung der Zeile aufheben:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 und fügen Sie die folgende Zeile hinzu:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 in die pkgundef-Datei der Anwendung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)   
 [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md)
