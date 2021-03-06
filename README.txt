# Release Version 1.0.1
# README / MANUAL
# DATABASE -DATA, ENCRYPTING SOFTWARE
# ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
#
# Manual for "settings.json" and general use of this program.
#
#>>> Please consider reading and filling the settings file properly before executing this program. <<<
#    ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
#>>  If you *"accidentally"* encrypt vital files from the database you may corrupt your database. <<
#          -*"You specifically enter system tables, and their columns into the list"*
#    
# Tested only on a FIREBIRD DATABASE, no quarantee of working in other database structures.
# *Works in databases, with same select and update syntaxes as firebird.
#
#
#
#> If you encrypt your database with a faulty password / forget your password,
#> there is a chance you end up encrypting your data as a 1 way ticket, without a chance to regain the data.
#
# >> Faulty password meaning, contains a character which is not supported in UTF-8, or other similar exception.
#
#
#
#> If you have a copy of the RECOVERY_KEYS.txt, that will be generated to the root folder with a time stamp
#> It is possible to recover the Hash Password by
#> sending your RECOVERY_KEY.txt LOG / specified key + some details to the author given below.
#
# ______________________________________________________
# |Creator, Owner, Developer, Author - Kokkarinen Ville|
# ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
# ____________________________
# |kokkarinen.ville@gmail.com|
# ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
##############################################################################################




#1
# Encrypt & Decrypt
#
# When encrypt is set as "true", attempts to encrypt data
#      ¯¯¯¯¯¯¯                               ¯¯¯¯¯¯¯
# When encrypt is set as "false", attempts to decrypt data
#      ¯¯¯¯¯¯¯                               ¯¯¯¯¯¯¯ 
#
# Type: Boolean
#
# Encrypt = true
# Encrypt = false




#2
# EditShortFields
#
# When EditShortFields is set as "true",
# will also edit fields that are too short to receive encrypted data back,
# with the value defined at "ValueForShortFields".
#
# Type: Boolean
#
# EditShortFields = true




#3
# ValueForShortFields
#
# When EditShortFields is set as "true" and "ValueForShortFields" has a value,
# edits fields that are too short to receive encrypted data back,
# with the value defined at "ValueForShortFields".
#
# Note: If this value is still too long to fit in a field, the field will not be encrypted, and will be left as it is found
# 
# Type: String
#
# ValueForShortFields = "XYZ"


#4
# FirebirdDB
#
# choose if database is SQL or Firebird based
#
# True = uses firebird syntaxes & connectionstring
# false = uses SQL syntaxes & connectionstring
#
# Type: Boolean
#
# firebirdDB = true
# firebirdDB = false

#5
# Connectionstring
#
# Required to connect to a database
# ¯¯¯¯¯¯¯¯
#
# Example. connectionstring:
# "User ID=sysdba;Password=admin;Database=192.168.0.1:C:/Databases/Database.fdb;Datasource=192.168.0.1;"
#
# Type: string
#
# connectionstring = ""




#6
# HashingPassword
#
# Password used to SHA256 hash data
# ¯¯¯¯¯¯¯¯
# Must be atleast 8 characters long
# ¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯¯
# Not necessary but preferably, 10+ characters long with 3 or more of the following categories:
# - Contains UPPERCASE letters
# - Contains lowercase letters
# - Contains numerals 0-9
# - Contains special characters: !"#¤%&/ etc.
# - Contains characters, which are not found on a keyboard, and can be generated
#   with certain ALT + number combinations.
#
#
# Note: Try not to include characters that are not supported by most platforms and or UTF-8
#       You may risk using a character that turns into something else when converted to UTF-8
#       *Some chinese/ japanese/ korean symbols etc. you can't find on a QWERTY keyboard.
#
# Type: string
#
# HashingPassword = "admin123!"




#7
# TableNames
# 
# Array of tables, to encrypt / decrypt
#          ¯¯¯¯¯¯
# The program fetches table(s) which are defined here
# 
# Note that each field requires a comma, if there is another record after it.
# 
# "TableNames":[
# "table1",
# "table2",
# "table3"
# ]




#8
# ColumnNames
# 
# Array of columns to encrypt/decrypt
#          ¯¯¯¯¯¯¯
# The program creates a list of all availabe columns entered here, from the tables defined above.
# If the column doesn't exist in the table, it's left out from the editing.
#
#
#
# Note that each field requires a comma, if there is another record after it.
# 
# "ColumnNames": [
# "Column1",
# "Column2",
# "Column3"
# ]
