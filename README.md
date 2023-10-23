# f5-bigip-next-vault
Start Vault in a new terminal
vault server -dev -dev-root-token-id root
2. Export an environment variable for the vault CLI to address the Vault server.

export VAULT_ADDR=http://127.0.0.1:8200
3. Export an environment variable for the vault CLI to authenticate with the Vault server.

export VAULT_TOKEN=root

vault write -field=certificate pki/root/generate/internal common_name="maniak.academy" ttl=87600h > CA_cert.crt

# Configure the CA and CRL URL
vault write pki/config/urls issuing_certificates="$VAULT_ADDR/v1/pki/ca" crl_distribution_points="$VAULT_ADDR/v1/pki/crl"