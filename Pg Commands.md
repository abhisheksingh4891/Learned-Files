To encrypt and decrypt password in PgSql

Install extension
CREATE EXTENSION IF NOT EXISTS pgcrypto;

select pgp_sym_encrypt(password, 'my_secret_key')

select pgp_sym_decrypt(Encrypted_password, 'my_secret_key')
