---
title: 'Vorgehensweise: Verbinden mit der Northwind-Datenbank | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connections [Visual Studio], Northwind database
- Northwind sample database
ms.assetid: cc6cb79f-d035-41f8-b398-8d4a45922bfb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3f64fa378029546f7a3126b324c282f6a91d7231
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897629"
---
# <a name="how-to-connect-to-the-northwind-database"></a>Gewusst wie: Verbinden mit der Datenbank Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Während Sie das Erstellen von Datenbankanwendungen mithilfe von Visual Studio lernen, müssen Sie eine Verbindung mit der Datenbank Northwind herstellen, um vielen der Beispielen in der Dokumentation für dieses Produkt zu folgen. Je nachdem, welchem Beispiel Sie folgen, müssen Sie eine Verbindung entweder mit einer Datenbank in SQL Server oder in einer Datenbankdatei, beispielsweise in einer für Microsoft Access oder SQL Server, herstellen.  
  
## <a name="creating-data-connections-to-the-northwind-database"></a>Erstellen von Datenverbindungen mit der Northwind-Datenbank  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-data-connection-to-the-northwind-database-sql-server"></a>So erstellen Sie eine Datenverbindung mit der Northwind-Datenbank (SQL Server)  
  
1. Auf der **Ansicht** Menü wählen **Server-Explorer**/**Datenbank-Explorer**.  
  
2. In **Server-Explorer**/**Datenbank-Explorer**, öffnen Sie das Kontextmenü für **Datenverbindungen** , und wählen Sie **"Verbindung hinzufügen"**.  
  
    Nach der Auswahl **Verbindung hinzufügen**, entweder die **Datenquelle auswählen** Dialogfeld oder **Verbindung hinzufügen** Dialogfeld wird angezeigt.  
  
3. Wenn die **Datenquelle auswählen** wählen Sie im angezeigten Dialogfeld **Microsoft SQL Server**, und wählen Sie dann **OK**.  
  
    Wenn die **Verbindung hinzufügen** Dialogfeld wird angezeigt, und die **Datenquelle** ist nicht **Microsoft SQL Server (SqlClient)**, wählen Sie die **Änderung** die Schaltfläche, um die **Datenquelle wechseln** wählen Sie im Dialogfeld **Microsoft SQL Server**, und wählen Sie dann die **OK** Schaltfläche.  
  
4. In der **Servernamen** aufzulisten, geben Sie den Namen des Servers, auf dem die Northwind-Datenbank gespeichert ist.  
  
5. Wählen Sie je nach den Anforderungen Ihrer Version von SQL Server und der Northwind-Datenbank, **Windows-Authentifizierung verwenden** oder **SQL Server-Authentifizierung** , und geben Sie einen Benutzernamen und Kennwort zum Anmelden auf des Computers mit SQL Server.  
  
6. Wählen Sie die Northwind-Datenbank in der **auswählen oder Eingeben eines Datenbanknamens** Liste.  
  
7. Wählen Sie **Testverbindung** um die Verbindung zur Northwind-Datenbank überprüfen.  
  
8. Klicken Sie auf **OK**.  
  
    Eine Datenverbindung zur Northwind-Datenbank wird hinzugefügt, um **Server-Explorer**/**Datenbank-Explorer**.  
  
   Außer dem Herstellen einer Verbindung mit einer Remoteinstanz einer SQL Server-Datenbank können Sie auch eine Verbindung direkt zu den eigentlichen Dateien herstellen, in denen sich die Datenbank befindet. Auf diese Weise können Sie die Datenbankdateien direkt einem Projekt hinzufügen, wo sie dann als Teil der Anwendung bereitgestellt werden können. Die folgenden lokalen Datenbankdateien werden derzeit unterstützt: SQL Server Compact-Datenbankdateien (.sdf), [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und SQL Server Express-Datenbankdateien (.mdf) und Microsoft Access-Datenbankdateien (.mdb oder .accdb).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databasesql-server-database-file-mdf"></a>So erstellen Sie eine Datenverbindung zur Datenbank Northwind – MDF-Datenbankdatei (SQL Server)  
  
1.  Auf der **Ansicht** Menü wählen **Server-Explorer**/**Datenbank-Explorer**.  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, öffnen Sie das Kontextmenü für **Datenverbindungen** , und wählen Sie **"Verbindung hinzufügen"**.  
  
     Nach der Auswahl **Verbindung hinzufügen**, entweder die **Verbindung hinzufügen** Dialogfeld oder **Datenquelle auswählen** Dialogfeld wird angezeigt.  
  
3.  Wenn die **Datenquelle auswählen** wählen Sie im angezeigten Dialogfeld **Microsoft SQL Server-Datenbankdatei**, und wählen Sie dann die **OK**.  
  
4.  Wenn die **Verbindung hinzufügen** Dialogfeld angezeigt wird, überprüfen Sie, ob die **Datenquelle** nastaven NA hodnotu **Microsoft SQL Server-Datenbankdatei (SqlClient)**. Wenn sie nicht, um festgelegt ist **Microsoft SQL Server-Datenbankdatei (SqlClient)**, wählen Sie **Änderung** zu öffnen der **Datenquelle wechseln** Dialogfeld wählen **Microsoft SQL Server-Datenbankdatei**, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Wählen Sie **Durchsuchen** um die MDF-Datei zu suchen, die Northwind-Datenbank enthält.  
  
6.  Je nach den Anforderungen Ihrer Version der Northwind-Datenbank, wählen Sie entweder **Windows-Authentifizierung verwenden** oder **SQL Server-Authentifizierung** , und geben Sie einen Benutzernamen und ein Kennwort zum Anmelden die Computer mit SQL Server.  
  
7.  Klicken Sie auf die Schaltfläche **OK** .  
  
     Eine Datenverbindung zur Northwind-Datenbank wird hinzugefügt, um **Server-Explorer**/**Datenbank-Explorer**.  
  
> [!NOTE]
>  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] umfasst Änderungen, die für die Northwind-Datenbankdatei (.mdf) gelten. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-a-data-connection-to-the-northwind-databaseaccess-database-file-mdb-or-accdb"></a>So erstellen Sie eine Datenverbindung mit der Northwind-Datenbank - Access-Datenbankdatei (.mdb oder .accdb)  
  
1.  Auf der **Ansicht** Menü wählen **Server-Explorer**/**Datenbank-Explorer**.  
  
2.  In **Server-Explorer**/**Datenbank-Explorer**, öffnen Sie das Kontextmenü für **Datenverbindungen** , und wählen Sie **"Verbindung hinzufügen"**.  
  
     Nach der Auswahl **Verbindung hinzufügen**, entweder die **Verbindung hinzufügen** Dialogfeld oder **Datenquelle auswählen** Dialogfeld wird angezeigt.  
  
3.  Wenn die **Datenquelle auswählen** wählen Sie im angezeigten Dialogfeld **Microsoft Access-Datenbankdatei**, und wählen Sie dann **OK**.  
  
4.  Wenn die **Verbindung hinzufügen** Dialogfeld angezeigt wird, überprüfen Sie, ob die **Datenquelle** nastaven NA hodnotu **Microsoft Access-Datenbankdatei**. Wenn sie nicht, um festgelegt ist **Microsoft Access-Datenbankdatei**, wählen Sie **ändern** zu öffnen der **Datenquelle wechseln** Dialogfeld wählen **Microsoft Access-Datenbank Datei**, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Wählen Sie **Durchsuchen** um die MDB- oder ACCDB-Datei zu suchen, die Northwind-Datenbank enthält.  
  
6.  Geben Sie einen Benutzernamen und ein Kennwort ein, wenn dies bei Ihrer Version der Datenbank Northwind erforderlich ist.  
  
7.  Klicken Sie auf **OK**.  
  
     Eine Datenverbindung zur Northwind-Datenbank wird hinzugefügt, um **Server-Explorer**/**Datenbank-Explorer**.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md)   
 [Datenprogrammierung mit Microsoft Access 2010](http://msdn.microsoft.com/library/office/ff965871.aspx)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)