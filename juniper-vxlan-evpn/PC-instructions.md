# Configuring the PCs (VPCS)

Each PC is a VPCS node. It has no configuration file of its own, so you set its address by typing commands into its console. The settings are saved when you run `save`.

## Before you start

- Start all four nodes and wait until both cores are booted and you can log in to them.
- Load the core configs first, so the gateways exist before you test them.

## CaliforniaPC

1. Open the console for CaliforniaPC in EVE-NG.
2. Type:

   ```
   ip 10.100.0.11/24 10.100.0.1
   save
   ```

3. Check the result:

   ```
   show ip
   ```

   You should see IP `10.100.0.11`, mask `255.255.255.0`, and gateway `10.100.0.1`.

4. Ping the gateway:

   ```
   ping 10.100.0.1
   ```

   You should see replies like `84 bytes from 10.100.0.1 icmp_seq=1 ttl=64`.

## NewYorkPC

1. Open the console for NewYorkPC in EVE-NG.
2. Type:

   ```
   ip 10.100.0.12/24 10.100.0.2
   save
   ```

3. Check the result:

   ```
   show ip
   ```

   You should see IP `10.100.0.12`, mask `255.255.255.0`, and gateway `10.100.0.2`.

4. Ping the gateway:

   ```
   ping 10.100.0.2
   ```

   You should see replies from `10.100.0.2`.

## What to expect in step 1

- Each PC can reach its own gateway. This is what success looks like.
- CaliforniaPC cannot reach NewYorkPC or NewYorkCore, and NewYorkPC cannot reach CaliforniaPC. This is expected. Both sites use the same 10.100.0.0/24 subnet, but nothing connects them yet. Step 2 fixes this.

Do not treat a cross-site ping failure as a configuration error in step 1.

## If a ping to the gateway fails

- Run `show ip` and confirm the address and gateway were typed correctly.
- Confirm the matching core is up and its `ge-0/0/1` interface is up. On the core, run `show interfaces terse | match ge-0/0/1`.
- Confirm the core has its step 1 config. On the core, run `show configuration interfaces ge-0/0/1`.
- Run `save` again on the PC. A PC that wasn't saved loses its address when the lab restarts.
