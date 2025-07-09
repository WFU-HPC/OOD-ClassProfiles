# OOD-ClassProfiles


`/etc/ood/config/ondemand.d/ondemand.yml`

```yaml
host_based_profiles: true
```


`/etc/ood/config/ood_portal.yml`

```yaml

# The server name used for name-based Virtual Host
# Example:
#     servername: 'www.example.com'
# Default: null (don't use name-based Virtual Host)
servername: login.cluster.edu

# The server aliases used for the name-based Virtual Host
# Example:
#     server_aliases:
#       - foo.example.com
server_aliases:
  - login.cluster.edu
  - sta379.cluster.edu
  - phy262.cluster.edu
  - phy266.cluster.edu
```


```sh
magick \
    "logo/LOGO_HPC.png" \
       -background Transparent \
       -gravity East \
       -extent 3800x520 \
       -font Bodoni-72-Smallcaps-Book \
       -fill black \
       -pointsize 500 \
       -gravity NorthWest \
       -draw 'text 0,-100 "OOD101"' \
       -pointsize 350 \
       -gravity Center \
       -draw 'text 0,0 "@"' \
    "ood101/logo-ood101.png"
```



```yaml
- name: 'openondemand profiles ood101'
  tags: 'openondemand_profiles_ood101'
  ansible.builtin.copy:
    src: "{{ item.src }}" 
    dest: "{{ item.dest }}"
    owner: root
    group: ood101
    directory_mode: "0750"
    mode: "preserve"
    force: true
  with_items:
    - src: "ood101/profile-ood101.yml"
      dest: "/etc/ood/config/ondemand.d/profile-ood101.yml"
    - src: "ood101/_widget_ood101.html.erb"
      dest: "/etc/ood/config/apps/dashboard/views/widgets/_widget_ood101.html.erb"
    - src: "ood101/logo-ood101.png"
      dest: "/var/www/ood/public/logo-ood101.png"
```


