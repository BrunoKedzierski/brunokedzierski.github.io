---
layout: post
title:  SQL Server - Transaction with try catch
categories: [Code, SQL]
---
General pattern for error handling on SQL Server

```
CREATE PROCEDURE insert_data @a int, @b int AS 
   SET XACT_ABORT, NOCOUNT ON
   BEGIN TRY
      BEGIN TRANSACTION
     -- Procedure code
      COMMIT TRANSACTION
   END TRY
   BEGIN CATCH
      IF @@trancount > 0 ROLLBACK TRANSACTION
      DECLARE @msg nvarchar(2048) = error_message()  
      RAISERROR (@msg, 16, 1)
      RETURN 9999999
   END CATCH
```