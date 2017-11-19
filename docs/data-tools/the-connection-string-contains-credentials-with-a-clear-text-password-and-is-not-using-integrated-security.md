---
title: "Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und ist nicht mithilfe der integrierten Sicherheit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: e9c03f6c864894d0dee9a0fade3137f1a7c50cda
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>Die Verbindungszeichenfolge enthält Anmeldeinformationen mit einem Klartext-Kennwort und verwendet keine integrierte Sicherheit.
Möchten Sie die Verbindungszeichenfolge mit vertraulichen Informationen in der aktuellen DBML-Datei und in den Anwendungskonfigurationsdateien speichern?  Klicken Sie auf Nein, um die Verbindungszeichenfolge ohne die vertraulichen Informationen zu speichern.  
  
 Beim Arbeiten mit Datenverbindungen, die vertrauliche Informationen enthalten (in der Verbindungszeichenfolge enthaltene Kennwörter) haben Sie die Option, die Verbindungszeichenfolge mit den vertraulichen Informationen oder ohne diese in der DBML-Datei und der Anwendungskonfigurationsdatei des Projekts zu speichern.  
  
> [!WARNING]
>  Das explizite Festlegen der **Verbindung** Eigenschaften **Anwendungseinstellungen** Eigenschaft **"false"** wird das Kennwort der DBML-Datei hinzugefügt.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge mit den vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Klicken Sie auf **Ja**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert. Die Verbindungszeichenfolge enthält die vertraulichen Informationen als Klartext. Die vertraulichen Informationen sind nicht in der DBML-Datei enthalten.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>So speichern Sie die Verbindungszeichenfolge ohne die vertraulichen Informationen in den Anwendungseigenschaften des Projekts  
  
-   Click **No**.  
  
     Die Verbindungszeichenfolge wird als Anwendungseinstellung gespeichert, jedoch ohne das Kennwort.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Nachrichten](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)