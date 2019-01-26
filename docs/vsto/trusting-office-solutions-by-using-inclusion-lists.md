---
title: Vertrauen Sie Office-Projektmappen mithilfe von Aufnahmelisten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b0e3df3562fe9a7bcbf2ca9cdc899b9303eb19a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868610"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Vertrauen Sie Office-Projektmappen mithilfe von Aufnahmelisten
  Mithilfe von Aufnahmelisten können Benutzer Office-Projektmappen, die mit einem Zertifikat signiert sind, das den Herausgeber identifiziert, Vertrauenswürdigkeit gewähren. Aufnahmelisten sind benutzerspezifisch und können für Anpassungen auf Dokumentebene und VSTO-Add-Ins verwendet werden.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Wenn ein Benutzer eine Office-Projektmappe startet, der keine Vertrauensstellung für diesen Benutzer gewährt wurde, wird er von der Microsoft Office-Projektmappe mit einer [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Vertrauensaufforderung zu einer Sicherheitsentscheidung aufgefordert. Wenn der Benutzer entscheidet, der Projektmappe zu vertrauen, wird die Anpassung ausgeführt, und beim nächsten Mal wird der Benutzer nicht zu einer Entscheidung aufgefordert.  
  
## <a name="inclusion-list-and-windows-installer"></a>Aufnahmeliste und Windows Installer  
 Installieren von Office-Lösungen in der *Programmdateien* Directory mithilfe von Windows Installer sind Administratorrechte erforderlich. Für Office-Projektmappen in der *Programmdateien* Verzeichnis, das Visual Studio-Tools für Office-Laufzeit überprüft nicht mehr die Aufnahmeliste, da die Office-Projektmappen FullTrust-Berechtigung bereits gewährt wurde.  
  
## <a name="clickonce-trust-prompt"></a>ClickOnce-Vertrauensaufforderung  
 Mit der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Implementierung für Office-Projektmappen können Administratoren die Vertrauensaufforderungsstufe so konfigurieren, dass Aufforderung aktiviert oder deaktiviert oder dass ein vertrauenswürdiges Zertifikat gefordert wird. Diese Konfiguration wird mit einem Registrierungsschlüssel vorgenommen, der den Zugriff auf die Aufnahmeliste steuert.  
  
 Ist Anzeigen der Aufforderung deaktiviert, können nur Projektmappen installiert werden, die ein vertrauenswürdiges und bekanntes Zertifikat haben. Ist die Aufforderungsstufe (PromptingLevel) so festgelegt , dass ein Authenticode erforderlich ist, muss die Projektmappe mit einem Zertifikat einer bekannten Zertifizierungsstelle signiert sein, es ist aber kein Zertifikat erforderlich, das zu einer vertrauenswürdigen Stammzertifizierungsstelle (einem vertrauenswürdigem Zertifikat) führt. Ist Anzeigen der Aufforderung aktiviert, kann die Projektmappe mit einem Zertifikat mit einer unbekannten Identität signiert sein. In diesem Fall wird die Entscheidung über die Vertrauenswürdigkeit an den Endbenutzer weitergegeben, und für die Installation der Projektmappe genügt ein temporäres Zertifikat.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der aufnahmelistensicherheit](../vsto/how-to-configure-inclusion-list-security.md) und Tabelle 2, Aufforderung Ebene Registry Key Value Launch Effects, im [ClickOnce konfigurieren vertrauenswürdiger Herausgeber](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="structure-of-the-inclusion-list"></a>Struktur der Aufnahmeliste  
 Ein gültiger Eintrag der Aufnahmeliste besteht aus zwei Teilen: einem Pfad zum Bereitstellungsmanifest und dem öffentlichen Schlüssel, der zum Signieren der Projektmappe verwendet wird. Nachdem eine Projektmappe zur Aufnahmeliste hinzugefügt wurde, wird sie als vertrauenswürdig eingestuft. Wenn die Office-Projektmappe ausgeführt wird, vergleicht die Office-Anwendung den öffentlichen Schlüssel in der Aufnahmeliste mit dem signierenden Schlüssel im Bereitstellungsmanifest, um zu überprüfen, ob die derzeit aktive Projektmappe mit der ursprünglich als vertrauenswürdig eingestuften Version identisch ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewähren von Vertrauen für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md)   
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
