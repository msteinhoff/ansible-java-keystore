# ansible-java-keystore

Ansible role which manages certificates in the default Java keystore.

# Dependencies

None.

# Role Variables

Available variables are listed below, along with default values (see
`defaults/main.yml`).  

All variables have set sensible defaults and usually should not need any
configuration.

## General settings

    java_keystore_jre_path: ""

Path to the keystore executable in the Java JRE.

Can be used together with `ansible-java-oracle-jdk`, e.g:

    java_keystore_jre_path: "{{ java_oracle_jdk_install_directory }}/jre"

---

    java_keystore_file_path: "{{ java_oracle_jdk_install_directory }}/jre/lib/security/cacerts"

File path to the keystore to manage. The Java default keystore can be found e.g. at:

    java_keystore_file_path: "{{ java_oracle_jdk_install_directory }}/jre/lib/security/cacerts"

---

    java_keystore_file_password: ""

The password for the keystore file.

Password for the default keystore is `changeit`.

    java_keystore_certificates:
    - certificate_file: "{{ playbook_dir }}/files/certificates/example.org"
      alias: example.org

A list of cetificates to manage.

# Example Playbook

    - hosts: keystore-hosts
      roles:
        - role: ansible-java-keystore

# License

MPLv2
