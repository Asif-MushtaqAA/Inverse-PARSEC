# Inverse-PARSEC
Reconstruct PARSEC parameters from given aerofoil coordinates.

To overcome the challenge of unavailable PARSEC parameters for existing aerofoils, an Inverse PARSEC approach is developed. 
This approach uses the L-BFGS-B optimisation algorithm to reconstruct PARSEC parameters from given aerofoil coordinates, allowing for parameter approximation when direct values are not available.

Methodology of Inverse PARSEC:
1. Optimisation Goal: The optimisation goal is to reduce the difference between the generated aerofoil shape and target aerofoil shape. This difference is quantified using a cost function, which the optimisation method aims to minimise.
2. L-BFGS-B Optimisation: The Limited-memory Broyden-Fletcher-Goldfarb-Shanno with Box Constraints (L-BFGS-B) is a powerful optimisation method that excels at addressing large-scale, bound-constrained optimisation problems. This method is appropriate for the Inverse PARSEC approach because it efficiently handles the huge number of variables involved in aerofoil shape optimisation while remaining within the parameters' physical constraints and uses limited amount of computer memory.
3. Process: The workflow was written in Python and optimised using the SciPy module. The L-BFGS-B algorithm iteratively adjusts the PARSEC parameters to minimise the difference between generated and target aerofoil coordinates. This process is repeated until the function tolerance of 2.22×10^(-9) or the maximum number of iterations 15000 is reached, resulting in a set of PARSEC parameters that closely resemble the target aerofoil.

Limitations:
The Inverse PARSEC approach is good at reconstructing aerofoil shapes from coordinate data. However, it struggles to accurately reconstruct aerofoils with camber exceeding 4% of the chord length, such as the NACA 6412.
