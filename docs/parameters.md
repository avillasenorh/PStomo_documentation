# Parameters

## Model parameters

- `h` = size of travel time basic cell, identical in the X, Y, and Z directions (km)
- `magX` = number of travel cells that a model cell has in the X direction
- `magY` = number of travel cells that a model cell has in the Y direction
- `magZ` = number of travel cells that a model cell has in the Z direction
- `nx` = number of model cells in the X direction (`xlen = nx * magX * h`)
- `ny` = number of model cells in the Y direction (`ylen = ny * magY * h`)
- `nz` = number of model cells in the Z direction (`zlen = nz * magZ * h`)
- `baseElev` = top of the model in km (negative if above sea level)
- `xmin` = left edge of the model in km (default = 0.0) __(not implemented!)__
- `ymin` = bottom edge of the model in km (default = 0.0) __(not implemented!)__

## Input files

- `srcfil` = station file (it is called "src" because stations are treated as sources in main code)
- `recvfil` = source file (it is called "recv" becuase sources are treated as receivers in main code)
- `obfile` = arrival time file
- `velfile` = binary file containing input/initial P-wave velocity model
- `velfile_s` = binary file containing input/initial S-wave velocity model

## Travel time parameters

- `maxres` = maximum P residual in seconds
- `maxsres` = maximum S residual in seconds

## Inversion parameters

- `invert` = flag to invert for velocity model: 1 = true, 0 = false
- `smoother` = smoothing constraint (small for rough model, high for smooth model)
- `ilsqr` = maximum number of LSQR iterations
- `max_cond_num` = maximum condition number for LSQR
- `truncater` = SVD truncater
- `UVout_flg` = flag to dump Ritz vectors to obtain resolution matrix: 1 = true, 0 = false
- `reortho_flg` = flag to reorthog. Ritz vectors (if `UVout_flg = 1`): 1 = true, 0 = false

## Earthquake parameters

- `no_shots` = flag to indicate that dataset contains no explosions: 1 = true (no explosions), 0 = false (explosions)
- `no_earthq` = flag to indicate that datasets contains no earthquakes: 1 = true (no earthquakes), 0 = false (earthquakes)
- `min_z` = 



## Vp/Vs parameters

- `swave_flg` = use S waves flag: 1 = true, 0 = false
- `vps_ratio` = Vp/Vs ratio (a priori?, use to regularize?)
- `ps_wght_type` = P/S wave weight flag: 0 = do not weight P and S residuals, 1 = weight based on variance, 2 = fixed weight
- `ps_wght` = weight to use when `ps_wght_type = 2`
p_res_var

## Output files

- `ttlog` = flag to ouput file with computed travel times `Traveltime.log`: 1 = true, 0 = false
- `eqinfo` = flag to output file with hypocenter errors: 1 = true, 0 = false

## To sort

- `xwt` = 
- `ywt` = 
- `zwt` = 
- `magz_u` = 
- `z_u_lim` = 
- `magz_l` = 
- `z_l_lim` = 
- `rel_only` = 
- `loc_only` = 
- `relative` = 
- `maxOffset` = 
- `minOffset` = 
- `errlog` = 
- `reslog` = 
- `raylog` = 
- `msd` = 
- `interpolate` = 
- `min_z` = 
- `max_dh` = 
- `max_dt` = 
- `app_var` = 
- `detail` = 
- `det_z` = 
- `det_magz` = 
- `reduce` = 
- `red_z` = 
- `red_magx` = 
- `red_magy` = 
- `red_magz` = 
- `variable_sm` = 
- `auto_cov_lim` = 
- `maxsmooth` = 
- `minsmooth` = 
- `maxcover` = 
- `mincover` = 
- `lnsmooth` = 
- `Podvin_Lecomte` = 
- `Podvin_Lecomte_msg` = 
- `shotstat` = 
- `max_stat` = 
- `velzone` = 
- `velzone_tres` = 
- `vps_ratio` = 
- `cross_grad` = 
- `cross_grad_horiz` = 
- `cross_grad_wght` = 
- `use_pert_file` = 
- `perturb_file` = 
- `perturb_file_s` = 
- `cross_grad_ext` = 
- `cross_grad_ext_horiz` = 
- `xg_ext_file` = 
- `cross_grad_ex_wght` = 
- `cross_grad_ext_ons` = 
- `cross_grad_ex_inv` = 
- `out_jacob` = 
- `out_res` = 
- `NETtomo` = 
- `NETmodel` = 
- `reg_only` = 
- `loc_pdf_use` = 
- `loc_pdf_name` = 
- `loc_pdf_nx` = 
- `loc_pdf_ny` = 
- `loc_pdf_nz` = 
- `loc_pdf_dx` = 
- `loc_pdf_dy` = 
- `loc_pdf_dz` = 
- `vel_pdf_use` = 
- `vel_pdf_name` = 
- `vel_pdf_nx` = 
- `vel_pdf_ny` = 
- `vel_pdf_nz` = 
- `vel_pdf_dx` = 
- `vel_pdf_dy` = 
- `vel_pdf_dz` = 
