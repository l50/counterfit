# DEMO 4: White-box attack of an on-disk

[[Demo Home]](README.md)

## Objective

Compare white-box and API attacks to digits model

## Threat Model

- Attacker knowledge: full access to model
- Security violation: integrity

1. List available targets

   ```bash
   list targets
   ```

2. Interact with `interact digits_keras`

   ```bash
   interact digits_keras
   ```

3. Look at a few digits

   ```bash
   predict -i range(20)
   ```

4. Load `art` and list possible attacks

   ```bash
   load art
   list attacks
   ```

5. Let's first try a whitebox attack `CarliniLInfMethod`

   ```bash
   use CarliniInfMethod
   ```

6. Set some parameters

   ```bash
   set --eps 0.15 --learning_rate 0.1 --max_iter 10 --sample_index 18
   ```

7. Run the attack

   ```bash
   run
   ```

8. Compare this with an API-only attack. We'll use `HopSkipJump`
   with default parameters.

   ```bash
   use HopSkipJump
   set --sample_index 18 --max_eval 1250 --max_iter 5 --norm inf
   run
   ```

## (Optional) Self Assessment

1. What are the model access requirements for `CarliniLInfMethod` vs. `HopSkipJump`?
2. Compare the visual quality of these two attacks?
   Which is better? Which attack shows lower "Max Absolute Change"?
3. Find a set of _best_ parameters for both `CarliniLInfMethod` and
   `HopSkipJump` that provides excellent visual quality with
   few "Total Queries". Can you find a set of parameters for
   `CarliniLInfMethod` that can't replicate the quality
   or efficiency with `HopSkipJump`?

[[Demo Home]](README.md)
