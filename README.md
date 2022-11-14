# Protect-deleting-a-row-with-id

# Run this trigger to block deleting users like super admins etc..

          DELIMITER $$

          CREATE TRIGGER trigger1
          BEFORE DELETE
          ON table1
          FOR EACH ROW
          BEGIN
            IF OLD.id = 1 THEN -- Abort when trying to remove this record
              CALL cannot_delete_error; -- raise an error to prevent deleting from the table
            END IF;
          END
          $$

          DELIMITER ;
